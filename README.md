# TIL

# Concurrent Hash Map (JAVA 동시성 처리 라이브러리)

# 객체지향
    추상클래스 vs 인터페이스
    추상 매서드 정의가 가능하고 그 자체로는 객체를 생성할 수 없는 공통점.

    추상(abstract)클래스
        상속의 개념 , 다중 상속 불가능(상위에서 하위는 가능)
            동물(추상클래스) 
            - 호랑이(상속) 
            - 토끼(상속)
        공통적인 기능들은 일반 메서드로 정의(호흡)
        공통적이지만 객체에 따라 다른 기능 추상 메서드로 정의( 먹기 - 육식, 초식)

    인터페이스
        기능을 장착 , 추상메서드만 정의 가능, 다중 구현 가능
        각각 다른 추상클래스(파리,비둘기)를 상속받는데 공통된 기능이 필요할때(날기)

    OVERRIDE,OVERLOAD
             

<details>
<summary>출처</summary>
https://myjamong.tistory.com/150
</details>


# TODO
* 스레드가 필요한 이유? https://jhnyang.tistory.com/368
* 자바 스레드
  
# REVIEW


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

    1. Minor GC : Young 영역에서 삭제
    Eden -> Survivor 0 -> Sruvivor 1 -> Old 반복
      * Survivor 0 -> Survivor 1 순서가 아님.
      * 0과 1을 번갈아가면서 적재하며 참조 횟수를 체크
      * 0과 1중 하나는 비어있는 상태
    Old 영역이 기준치 이상 차게되면 Full GC가 발생

    Major GC(Full GC) : Old 영역 에서 삭제
    - Minor GC 보다 훨씬 많은 시간 (메모리 크기가 큼)
    - 실행 중 GC를 제외한 모든 Thread 일시정지(Stop the world)
        * Young GC 중에도 멈추긴 하지만 무시할 만한 수준
    - 객체를 삭제하면 Heap 영역에 빈 메모리 공간이 생겨 이를 없애기 위해 메모리 전체를 재구성함.
        * GC에 포함, GC가 끝나고 재구성 하는것이 아님
        * Young GC도 GC중 재구성함
  
    #GC 알고리즘
    G1 GC
  
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


<details>
<summary>출처</summary>

https://2ssue.github.io/base/190509_PJI/    
https://doozi0316.tistory.com/  
https://coding-nyan.tistory.com/85  
https://beststar-1.tistory.com/3  
민국님

</details>
