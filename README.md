# TIL

# JVM
    - OS에 종속받지 않고 자바(Java Byte Code)를 실행하기 위한 가상 기계
    - 내부에서 메모리 관리가 가능
    - 크게 3가지 구조
      * Class Loader
      * Excution Engine (Interpreter,JIT Compiler,Garbage Collector)
      * Runtime Data Area

## * JIT(just-in-time compilation) 컴파일러
    인터프리트 방식 : Runtime 시 한줄씩 변환
    정적 컴파일 방식 : Runtime 전 미리 기계어로 변환
    JIT 컴파일(동적 번역) : 인터프리터 + 정적 컴파일

    * 각각 명령어 단위로 본다면 인터프리트 방식이 빠르지만 전체 코드로 본다면 컴파일 방식이 빠름.

    인터프리트 방식에서 같은 코드를 매번 기계어로 번역하는것을 방지
    메서드 호출 시 횟수를 누적해서 특정 수치(컴파일 임계치)를 초과하는 것만을 컴파일, 캐싱해 두었다가 사용.


## * Garbage Collector

    Runtime Data Area > Heap 메모리 영역에 적재된 객체 중 참조되지 않은 객체들을 제거

    Minor GC : Young 영역에서 삭제
    Eden -> Survivor 0 -> Sruvivor 1 -> Old 반복
    Old 영역이 기준치 이상 차게되면 Full GC가 발생

    Major GC(Full GC) : Old 영역 에서 삭제
    - Minor GC 보다 훨씬 많은 시간 
    - 실행 중 GC를 제외한 모든 Thread 일시정지(Stop the world)
    - 객체를 삭제하면 Heap 영역에 빈 메모리 공간이 생겨 이를 없애기 위해 메모리 전체를 재구성함.
  
    #GC 알고리즘
  
    OOM(Out Of Memory)
    할당된 메모리의 공간을 모두 사용하여, 새로 메모리 공간을 할당할 여유가 없다는 뜻.
    메모리 누수, Static 변수가 너무 많을 경우 주로 발생

# JAVA 코드의 실행과정
    1. .Java 파일이 Java Compiler에 의해 .Class파일로 변환(Java Byte Code)
    2. Class Loader가 .Class 파일을 JVM으로 로드해 Runtime Data Area에 배치
    3. Excution Engine에 의해 Binary Code로 변환해 실행 
       1. 인터프리터에 의해 명령어 단위로 변환해 실행
       2. 적절한 시점에 JIT Compiler에 의해 Byte Code 전체를 컴파일하여 실행
       3. 이후는 더이상 인터프리팅 하지 않음.
    4. 가비지 콜렉터

# TODO
* 스레드가 필요한 이유? https://jhnyang.tistory.com/368
* 자바 스레드
  
# REVIEW
