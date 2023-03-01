# BigDecimal

## BigDecimal 이란?
BigDecimal은 임의 정밀도 십진 산술을 제공하는 Java 프로그래밍 언어의 클래스이다.  
이는 고정 비트 수와 제한된 정밀도를 갖는 int 또는 double과 같은 Java의 다른 숫자 데이터 유형과 달리 모든 크기 및 정밀도의 십진수를 처리할 수 있다.

## 왜 사용하는거야?
다른 숫자 데이터 유형에 비해 BigDecimal을 사용하는 주요 이점 중 하나는 정밀도이다.  
예를 들어 double 또는 float로 계산을 수행할 때 이러한 유형의 제한된 정밀도로 인해 결과가 정확하지 않을 수 있으나,  
BigDecimal은 원하는 정밀도로 정확한 결과를 반환한다.

정확성이 중요한 금융 및 통화 어플리케이션 이나 과학 및 엔지니어링 응용분야에서도 사용한다.

## 어떻게 사용해?

- ### JAVA

    ```java
    BigDecimal bigDecimal = new BigDecimal("123.456");
    ```

    초기화 할때 문자열의 형태로 생성자에게 전달해 인스턴스를 만들어 사용한다.  
    int, double 타입 그대로 전달할 경우 예상과 다른 값을 얻을 수있으니 주의하자

    ```java 
    // 비교함수들

    BigDecimal a = new BigDecimal("10.0");
    BigDecimal b = new BigDecimal("3.0");

    a.add(b); // 더하기
    a.subtract(b); // 뺴기
    a.multiply(b); // 곱하기
    a.divide(b, 2, RoundingMode.HALF_UP); // 나누기
    a.remainder(b, MathContext.DECIMAL128) // 나눈 후 나머지 (전체자리 34로 제한)
    new BigDecimal("-1").abs(); // 절대값
    a.min(b); // 두 수 중 최소값
    a.max(b); // 두 수 중 최대값
    ```

- ### SQL
    ```sql
    CREATE TABLE my_table (
    id INT PRIMARY KEY,
    value DECIMAL(10,2)
    );
    ```
    위 쿼리에서는 id, value의 열을 같고있는 my_table을 생성하고  
    value에 지정된 DECIMAL(10,2) 은 최대 10자리, 소수점2자리를 저장할 수 있다.

## 주의 사항
하지만 BigDecimal은 더 복잡한 데이터 유형이므로 다른 숫자 데이터 유형보다 속도가 더 느리고 더 많은 메모리가 필요할 수 있으므로 성능이 중요한 애플리케이션에서는 신중하게 사용해야한다.

## Note
- 2023-03-01 첫 발행
    > 정산 프로젝트를 하며 BigDecimal 타입을 처음 사용해봐서 간략하게 정리해보았다.
    찾아보니 소수점, 나누기 처리 값은 여러 메서드도 제공하는것 같다..
