# JAVA 기본 라이브러리



## String

- **toString()**

  - 문자열 형태로 사람들이 이해하기 쉬운 객체 정보 제공
- 패키지명.클래스명 + '@' + 16진수
  - 다른 클래스 오버라이딩 가능 - 사용자 객체 출력 값 정하는 메소드

- **`==` vs `equals()`**

  - `==` : 주소값 비교

  - `equals()` : 문자열 내용값 비교

    객체를 새로 생성했을 경우 `equals()`를 써도 내용 비교가 되지 않는 경우 있음

    이럴 때 오버라이딩을 통해 해결 가능

- **equalsIsIgnoreCase()**

  - 문자열 대소문자 구분하지 않고 동등성 비교

- **toUpperCase() / toLowerCase()**

  - 대문자 / 소문자 변경

- **문자열.length()**

  - 문자열의 길이 (공백 포함)

- **split("/")**

  - 큰 문자열을 지정 문자로 구분 분리

  ```java
  String address = "서울시 강남구 역삼동 선릉캠퍼스";
  String[] details = address.split(" ");
  ```

- **String Tokenizer**

  - String을 token 단위로 분리

  ```java
  StringTokenizer st = new StringTokenizer
  ("서울시 강남구 역삼동 선릉캠퍼스","");
  ```

  - StringTokenizer("쪼개져야 할 문자열", "쪼개는 기준");

- **concat()**

  - 두 문자열 합침

- **indexOf()**

  - 내부에 특정 문자가 몇번째 위치에서 발견되었는지 int 타입으로 리턴
  - 발견되지 않으면 -1 리턴
  - 첫번째 문자 = 0

- **substring(a,b)**

  - 특정 인덱스 범위 내의 부분 문자열 리턴
  - a, b는 int
  - 인덱스는 0부터 시작
  - a번 인덱스부터 b번 인덱스 이전까지의 문자열 리턴

- **st.hasNext()**

  - 분리 다음 데이터 존재
  - true / false 값 리턴

  ```java
  while(st.hasNext()) {
  	
  }
  ```

- **java.text.DecimalFormat**
  
  - 숫자 + 양식 -> 문자열

---

### 날짜 시간 표현

- **java.util.Date**

  - 시간이 지나면서 늘어나는 오차 때문에 대부분의 메소드가 곧 폐기될 예정

    (Deprecated API)

  - Calendar 메소드로 대부분 기능이 이식됨

  - Date(long)

    1970년 1월 1일 9시 기준 1/1000초씩 증가한 수
- **java.util.Calendar**
  
  - DAYOFMONTH, HOUROFDAY 등의 메소드 있음
- **java.text.SimpleDateFormat**
  
  - 국가, 개인, 컴퓨터 별로 날짜 시간 양식이 다르다
  - 따라서 개인에 맞게 국제 표준시간의 양식을 변환해줌
  - "yyyy - MM - dd (E) - HH : mm : ss " -> "연도 - 월 - 일 (요일) - 시간 : 분 : 초 "

- **DecimalFormat**
  - #.## -> 0의 자리가 마지막에 올 경우 생략
  - 0.00 -> 0의 자리가 마지막에 올 경우 0을 표현
  - 0.0#과 같이 혼용하여 사용 불가

