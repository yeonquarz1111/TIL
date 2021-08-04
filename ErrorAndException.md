# 예외처리 / 오류

## 오류

- **컴파일 오류**

  - 프로그램 작성시 빨간색 표시
  - 실행 도중 오동작

  ```JAVA
  int i = 3.14;
  ```

- **실행 오류**

  1. **프로그래머 제어 X**

     java virtual machine (jvm)

  2. **프로그래머 제어 O**

     ```java
     int i = Integer.parseInt(args[0]);
     System.out.println(100/i);
     ```

     args[0] -> "0" 입력한 경우

     정수를 0으로 나눌 수 없으므로 에러 발생

## 예외처리

- 오류가 난 경우 프로그램 중단
- 오류가 나더라도 프로그램 실행 & 오류 원인 해결 위해 예외처리



### 예외처리 구문

#### try

```java
try { 
	int i = Integer.parseInt(args[0]);
	int j = Integer.parseInt(args[1]);
	System.out.println(i/j);
}
```

- 예외 발생 가능성 문장
- 예외 발생시 catch 문 수행
- 예외 발생하지 않을 시 try 문 정상 수행

#### catch

```java
catch(ArithmeticException e) {
//try 수행 도중에 ArithmeticException 발생하면 catch 블록 대체 수행 지속
	System.out.println("다음부터는 0 입력 제외하세요");
// e.printStackTrace(); db, 파일입력
}
    
catch(ArrayIndexOutOfBoundsException e) {
	System.out.println("2개 이상의 값을 입력하세요");
}
  
catch(NumberFormatException e) {
	System.out.println("정수로 변경 가능 값을 입력하세요");
}
```

- try 수행 중 오류 발생하면 catch의 대체 블록 수행하라
- 오류마다 다른 catch 문을 사용할 수 있음

```java
catch(ArrayIndexOutOfBoundsException | NumberFormatException | ArithmeticException e) {
	System.out.println("3개 예외 동일 처리");
}
```

- 위와 같이 여러 종류의 예외를 동일하게 처리할 수 있음

```java
catch(Exception e) {
	System.out.println("예외 동일 처리");
}
```

- 모든 종류의 오류를 동일하게 처리할 수 있음

#### finally

```java
finally {
 System.out.println("예외가 발생해도 이 문장은 항상 출력");
}
```

- 예외가 발생해도 해당 내용을 항상 수행함

#### throws

```java
메소드명 throws 오류코드 {
    
}
```

- 메소드에서 처리하지 않은 예외를 다른 곳으로 떠넘긴다

```java
class A {
void test(int i) throws ArithmeticException { 
    // 매개변수 = 외부로부터 호출시 전달받아 사용하는 함수
	int j = 100;
	System.out.println(j/i);
}

void test2 () {
	try {
		test(0);
	} catch(ArithmeticException e) {
		System.out.println("0 전달 불가능");
	}
}
```