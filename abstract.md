# abstract

```java
class 도형 {

	abstract void 면적(); // 구체적인 구현부가 없음. 면적에 따라 구현부가 다양하기 때문

}
```

- abstract 클래스 

  - abstract 메소드 1개 이상 포함하는 클래스에 붙인다

- abstract 메소드

  - 선언부는 있고 구현부는 없는 메소드에 붙인다
  - 객체 생성 금지
  - 상속, 오버라이딩 의무화 - 하위클래스에서 메소드 오버라이딩 통해 구현부 정의해야 함
  - final 과 동시에 사용 불가 - 의미에 모순, error

  ```java
  final abstract void m()
  
  final abstract class A
  
  → final은 오버라이딩 금지, abstract 는 오버라이딩 필수
  
  → 의미에 모순, error
  
  public static final int i = 10;
  
  → ok
  ```



#### 도형 예제

```java
class 도형 {

    String name = "도형";

    abstract void 면적();

    abstract void 둘레();

    void tellName() { s.o.p(name); }

}

class 원 extends 도형 {

    abstract void 면적() { 3.14 * 반지름 * 반지름; }

    abstract void 둘레() {3.14 * 반지름 * 2; }

}

class 사각형 extends 도형 {

    abstract void 면적() { 가로 * 세로; }

    abstract void 둘레() { (가로+세로) *2; }

}  // 면적, 둘레 메소드 반드시 오버라이딩 해야 함
```

