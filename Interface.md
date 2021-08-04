# Interface

1. 다중상속 구현
2. public abstract 메소드만 선언 가능
3. 객체생성 불가능 = 생성자 없음 (기본 생성자도 없음)
4. public final static 필드변수 자동 선언
5. default 메소드 / static 메소드 -> jdk 1.8 추가된 문법
6. 클래스 implements 인터페이스 -> 클래스는 인터페이스를 상속받음

```java
class A {}

interface C {}

interface D {}

class B extends A implements C, D {}
```

- 자바는 클래스 2개 이상 상속 불가능

- 클래스 B는 **인터페이스 상속 메소드 오버라이딩 의무화**

  클래스 A 상속 메소드 오버라이딩은 선택

```JAVA
B b1 = new B();
```

- 상속, 오버라이딩, 추가 등 모든 메소드 사용 가능

```JAVA
A a1 = new B();
```

- B(상속, 오버라이딩 메소드) + A(상속 그대로 메소드)

```JAVA
C c1 = new B();
```

- B(상속 모든 메소드 오버라이딩 의무) + C(상속 그대로 메소드 구현 불가, 사용 불가)

### 인터페이스 쉽게 만들기

- 클래스 만들 때 인터페이스 옆 add 클릭
- 인터페이스 선택
- 자동으로 인터페이스 implements 들어감

