# ***MyBatis*** 

    - 자바에서 데이터베이스 프로그래밍을 좀 더 쉽게 할 수 있게 도와 주는 개발 프레임 워크이다.

    - java beans 객체를 preparedStatement parameters와 ResultMaps로 쉽게 매핑을 할수 있도록 도와준다.

    - 이를 통해 database에 접근하기 위한 자바 코드의 양을 줄일 수 있다. 

## 어떻게 실행 될까?

1. 객체를 파라미터로 전달
   - javaBeans, Map or primitive Wrapper

2. 매핑되는 sql 문장을 수행  
    - sql Maps 프레임워크는 PreparedStatement 인스턴스 생성  
    - 객체로부터 제공되는 값들을 파라미터로 세팅

3. SQL 문장을 수행하고 ResultSet으로부터 결과 객체를 생성.  
    - Update의 경우에는 영향을 받은 rows 수가 반환된다.  
    - 쿼리의 경우 하나 혹은 여러 객체들이 반환된다.

## ParmeterType
> 구문에 전달될 파라미터의 패키지 경로를 포함한 전체 클래스명이나 별칭

MyBatis에서 ParmeterType속성을 사용해서 해당 파라미터의 자료형을 명시해준다.  
Java에서 보낼 타입을 인지시켜주고, 쿼리에서 보낸 타입의 객체,변수,...을 사용한다.

![](/MyBatis1-1.png) 

위 이미지는 parameter로 String 타입을 보낼거라고 인지시켜주고, 쿼리에 적용한 모습이다.  실제 적용되는 ${} 안 parameter는 자바의 변수(객체)명과 일치시켜줘야 한다.  
Ex) String parameter = "test";

## ResultType
> 이 구문에 의해 리턴되는 기대타입의 패키지 경로를 포함한 전체 클래스명이나 별칭. collection인 경우 collection 타입 자체가 아닌 collection 이 포함된 타입이 될 수 있다. resultType이나 resultMap을 사용하라.


## String Substitution(문자열 대체)
- #{}
- ${}