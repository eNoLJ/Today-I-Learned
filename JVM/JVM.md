## **JRE (Java Runtime Enviroment)**

- JVM + 라이브러리
- JRE는 JVM과 JVM이 자바 프로그램을 동작 시킬 때 필요한 라이브러리를 포함하고 있다. 즉, JRE는 JVM의 실행 환경을 구현한 것이라 볼 수 있다.

</br>

## **JDK (Java Development Kit)**

- JRE + 개발도구
- JDK는 JRE와 Java 개발에 필요한 개발 도구(javac, javap 등)가 포함되어 있다. 즉, JRE는 실행만 한다면 JDK는 개발까지 포함한다.

</br>

## **JVM (Java Virtual Machine)**

JVM은 크게 3가지 구성되어 있다.

### **1. Class Loader Subsystem**

**역할**

java 파일(.java)을 javac를 이용하여 컴파일하면 byte code 타입 파일(.class)이 되는데 이 클래스 파일을 메모리(Runtime Data Areas)에 로딩

**특징**

- 동적 클래스 로딩 가능

  모든 클래스를 한번에 로딩하는 것이 아닌 필요한 클래스만을 필요한 시점에 로딩이 가능하다.

- Loading

  클래스 로더는 클래스 정보(FQCN)를 메모리에 담는다.

  FQCN : class path까지 합쳐진 class name

- Linking

  클래스 파일이 제대로 되었는지 검사

  Linking 과정을 통해 정적변수를 기본값(ex int = 0)으로 초기화

- Initialization

  정적변수를 초기값(ex int = 25(사용자 정의))으로 저장

  static block 실행

  -> new를 이용한 생성자보다 static block이 빨리 실행 됨. static block은 class loader에서 실행을 하고, 생성자는 힙 메모리에 올라갈 때 실행되기 때문

### **2. Runtime Data Areas**

**역할**

class loader를 통해 전달된 정보들을 각각의 메모리에 저장한다.

**특징**

- 메소드 영역 (method area)

  힙, 스택, pc 레지스터에 올라가는 정보 외의 정보들이라 생각하면 편하다.

  클래스 정보(FQCN, 이름이나 필드 관계 등), 정적 변수(클래스 로더가 로딩 할 때 저장), byte code 등

  메소드 영역은 1개

- 힙 영역 (heap area)

  객체, 배열, 이넘, 인스턴스 변수(코드에 new를 만났을 때 저장) 등

  힙 영역은 1개

- 스택 영역 (stack area)

  메소드, 지역변수 등

  스택 영역은 스레드의 개수만큼 존재

- pc 레지스터 (pc registers)

  각각의 프로그램이 어디까지 실행 되었는지 알려준다. 스레드가 여러개라면 context switching이 일어나기 때문에 각각의 스레드가 얼만큼 실행 되었는지 알 필요가 있다.

### **3. Execution Engine**

**역할**

자바를 동작시키는데 필요한 프로그램을 담고 있으며, 메모리(Runtime Data Areas)에 올라와 있는 파일을 실행한다.

**특징**

- Interpreter

  byte code를 기계가 이해할 수 있도록 native code로 바꾸는 작업을 한다.

  byte code를 한줄씩 변환을 하기 때문에 중복되는 코드도 매번 컴파일을 진행하게 되어 비효율 적이고 시간이 오래 걸린다.

- JIT (Just In Time) Compiler

  interpreter의 효율을 높히기 위해 JIT Comiler가 도입되었는데 도입 후 성능이 월등히 좋아졌다.

  interpreter가 반복되는 코드를 발견하면 JIT 컴파일러는 반복되는 코드를 native Code로 바꾼다. 그렇게 되면 반복된 byte code는 native Code로 바뀌어 있기 때문에 interpreter가 바로 사용할 수 있게 된다.

- Garbage Collection

  힙 영역에 있어서 필요 없어진 정보들을 처리한다.

  각각의 참조를 카운트하여 카운트가 0이면 참조가 되지 않는 불필요한 정보라 판단하여 없앤다.
