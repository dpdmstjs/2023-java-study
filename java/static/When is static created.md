# static은 언제 생성될까?

  static변수는 인스턴스가 생성될 때 만들어지는 변수가 아니다. 그렇다면 static은 언제 만들어질까?

![static](/img/static/static.jpg)

- 프로그램이 메모리에 올라가게 되면 프로세스가 되는데(프로그램이 메모리에 올라가면 프로세스가 되는 `인스턴스화`가 일어나게 됨) 프로세스에 올라가게 될 때 운영체제가 적절한 메모리를 할당하는데 그림에 있는 `process memory 구조` 기반으로 활당된다.

- static은 constant pool(상수, 리터럴)과 함께 처음 프로그램이 `메모리에 로딩될 때` 처음부터 `Data 영역`에 메모리를 잡게 된다. 

- Java 동작 과정으로 보면 static은 `compile time` 즉 컴파일러에 의해 소스코드가 바이트코드로 바뀌는 시점에 바인딩 되어 모든 값을 알고 있고 그 다음에 `JVM run time`인 `class Loder`에 의해 Runtime Data Area의 Method Area영역에(static Area) `Class Varible`에 저장되어 공유된다.

