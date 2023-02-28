# **_Exception Handling(예외처리)_**

## 예외처리의 개념 및 중요성

> 프로그램 실행 시 발생할 수 있는 예외에 대비하는 것으로 프로그램 비정상 종료를 막고 실행상태를 유지하는 것

- ### Error(에러) VS Exception(예외)

  프로그램을 돌렸을 때 오작동이나 비정상적으로 종료되는 원인을 오류나 에러라고 합니다. 이 에러는 '컴파일 에러'와 '런타임 에러'로 나눌 수 있는데, 글 자 그대로 컴파일 시 발생하는 에러와 실행 도중에 발생하는 에러를 뜻합니다. 일반적으로 컴파일러가 컴파일 에러를 통해 소스코드의 기본적인 검사를 마친다고 해서 실행 시에도 에러가 발생하는 것은 아닙니다. 실행 도중의 잠재적 오류까지 검사할 수 없기 때문에 컴파일이 잘 이루어졌어도, 실행 도중에 잘못된 결과를 얻거나 비정상 종료가 될 수 있는 것이죠.

  자바에서는 실행 시 발생할 수 있는 오류를 '에러(error)'와 '예외(exception)' 두 가지로 구분합니다. 에러는 메모리 부족, 스택오버플로우와 같이 발생하게 되면 복구할 수 없는 심각한 오류이고, 예외는 발생하더라도 수습할 수 있을 정도의 비교적 덜 심각한 오류입니다. 에러는 발생 시 막을 방도가 없지만, 예외는 프로그래머가 예외처리를 통해서 비정상종료를 막을 수 있는 것이죠.  
   [참조](https://itmining.tistory.com/8)

  즉,  
   **Error(에러)** : 발생시 수습할 수 없는 심각한 오류  
   **Exception(예외)** : 예외 처리를 통해 수습할 수 있는 오류

## 예외처리 방법

- ### try-catch-finally 구문

  > Java는 try-catch [-finally] 블록을 사용하여 예외를 처리하는 매커니즘을 제공한다.

  `try` : 예외가 발생할 수있는 코드를 포함  
   `catch` : 예외가 발생하면 예외를 처리  
   `finally` : 예외 발생 유/무와 상관없이 실행

  ```java
  try {

  // 예외를 모니터링할 코드 블록
  int result = 10 / 0; //  ArithmeticException이 발생

  } catch (ArithmeticException e) {

  // ArithmeticException을 처리하기 위한 예외 핸들러 블록
  System.out.println("An error occurred: " + e.getMessage());

  } finally {

      // 예외 발생 여부에 관계없이 실행될 마지막 블록
  System.out.println("This code will always be executed.");

  }
  ```

- ### throws 키워드

  특정 예외를 발생시킬 수 있음을 선언하고, 메서드 서명(시그니처)에 사용되며  
   그 뒤에 메서드가 throw할 수 있는 예외의 이름이 나온다.

  ```java
  public void myMethod() throws Exception {
    // 예외를 발생시킬 수 있는 메서드 코드
  }
  ```

  자신을 호출한 상위 메서드로 에러를 던짐 -> 어디까지? 잡아서 처리할때 까지

- ### throw 키워드

  매서드 내에서 예외를 고의로 발생 시킴

  ```java
  throw new 예외("예외 메시지")
  ```

  위 예제는 "예외 메시지" 메시지와 함께 Exception 클래스의 새 인스턴스를 만들고 메서드 내에서 throw합니다. 이는 특정 오류 조건에 대해 특정 예외를 발생시키려는 경우에 유용하다.

- ### 사용자 정의 예외

  - Class 정의

  ```java
  public class MyException extends Exception {
      public MyException() {
          super();
      }

      public MyException(String message) {
          super(message);
      }

      public MyException(String message, Throwable cause) {
          super(message, cause);
      }

      public MyException(Throwable cause) {
          super(cause);
      }

  }

  ```

  위 코드와 같이 `Exception` 이나 하위 클래스를 상속받아 사용자 정의 예외를 정의 할 수있다.  
  `Exception` 이 클래스에는 메시지 및/또는 원인이 있거나 없는 예외 인스턴스를 만들 수 있는 네 개의 생성자가 있다.

  - 예외던지기

  ```java
    public void myMethod() throws MyException {
        // My Exception을 발생시킬 수 있는 일부 코드
        if (someCondition) {
            throw new MyException("문제가 발생했습니다!");
        }
    }
  ```

  위 코드내에서 특정 요건이 true라면 메서드 내에서 인스턴스를 생성해 던진다.

**이처럼 사용자 지정 예외를 정의하면 코드의 오류 및 예외를 더 잘 처리하는 데 도움이 되는 보다 의미 있고 구체적인 예외를 만들 수 있다.**

## 예외 처리 시 주의사항

- 항상 예외 처리를 하자
- 의미있는 오류 메시지를 작성하자
- 예외를 맹목적으로 포착하지 말자
  > 단일 catch 블록에서 모든 예외를 잡지 말자
- 예외를 기록하자
  > 로깅 시스템을 활용해 예외를 파일이나 콘솔에 기록
- 예외를 무시하지 말자
- 사용자 정의 예외를 잘 사용하자

## Note

- 2023-02-28 첫 발행
  > 예외를 너무 가볍게? 배워 알고있던 것 같아 다시 한번 공부하며 기록
