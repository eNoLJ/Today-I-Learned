## 1. 단일 책임 원칙 Single Respondiblity Principle

- 소프트웨어의 설계 부품(클래스, 함수 등)은 단 하나의 책임만을 가져야 한다.

</br>

## 2. 개방 폐쇄 원칙 Open Closed Principle

- 기존의 코드를 변경하지 않고 기능을 수정하거나 추가할 수 있도록 설계해야 한다.

</br>

## 3. 리스코프 치환 원칙 Liskov Substitution Principle

- 자식 클래스는 부모클래스에서 가능한 행위를 수행 할 수 있어야 한다.

</br>

## 4. 의존 역전 원칙 Dependency Inversion Principle

- 의존 관계를 맺을 때, 변화하기 쉬운것 보단 변화하기 어려운 것에 의존해야 한다는 원칙이다.

* 변화하기 쉬운 것 : 구체적인 것, 구체화 된 클래스
* 변화하기 어려운 것 : 추상적인 것, 추상클래스나 인터페이스

</br>

## 5. 인터페이스 분리 원칙 Interface Segregation Principle

- 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야한다. 하나의 일반적인 인터페이스보다는 여러 개의 구체적인 인터페이스가 낫다.
