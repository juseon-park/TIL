# TIL

# JVM
    * OS에 종속받지 않고 자바(Java Byte Code)를 실행하기 위한 가상 기계
    * 내부에서 메모리 관리가 가능
    * 크게 
      * Class Loader
      * Excution Engine (Interpreter,JIT Compiler,Garbage Collector)
      * Runtime Data Area

## * JIT 컴파일러

## * Garbage Collector

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
