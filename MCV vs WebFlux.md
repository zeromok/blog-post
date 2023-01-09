# **_MVC 와 WebFlux의 차이점_**

> "기본 MVC가 벽에다 공던지고 공받기라면, WebFlux는 공을 기차에 실어보낸 후, 한 바퀴 돌아서 공을 내려준다."

## Spring MVC 또는 WebFlux를 사용하는 경우

1.  이미 작동중인 Spring MVC 애플리케이션이 있다면 Spring WebFlux로 변환 할 필요가 없으며, Spring MVC는 작성하고 디버그하는 쉬운 방법 인 명령형 프로그래밍을 사용합니다.

2.  non-blocking 웹 스택을 생성하고자한다면, 선택 가능한 서버 (Netty, Tomcat, Jetty, Undertow 및 Servlet 3.1+ 컨테이너)를 제공하는 Spring WebFlux를 선택할 수 있습니다. 웹 엔드 포인트) 및 반응 라이브러리 (Reactor, RxJava 또는 기타)를 선택할 수 있습니다.

3.  Spring WebFlux는 Java 8 lambda 또는 Kotlin과 함께 사용하는 가볍고 기능적인 웹 프레임 워크에 유용합니다.

4.  마이크로 서비스 애플리케이션에서 우리는 Spring MVC와 Spring WebFlux 컨트롤러의 혼합 애플리케이션을 가질 수 있습니다. Spring WebFlux 엔드 포인트도 가질 수 있습니다.

5.  애플리케이션이 JPA, JDBC 또는 네트워킹 API에 의존하는 경우 Spring MVC가 최선의 선택이다.

        (Webflux 는 Asynchronous Non-blocking I/O 을 방식을 활용하여 성능을 끌어 올릴 수 있는 장점이 있다.
        그런데 이 말은 즉, Non Blocking 기반으로 코드를 작성해야 한다.
        만약 Blocking 코드가 있다면 Webflux를 사용하는 의미가 떨어지게 된다.
        얼마 전까지는 Java 진영에 Non Blocking 을 지원하는 DB Driver가 없었지만,
        최근에 R2DBC 가 릴리즈되어 이제는 Java 에서도 Non Blocking 으로 DB 를 접근할 수 있게 되었다.)

## Spring MVC

> Spring MVC는 Sychronouse(동기적)으로 동작하는 Blocking(블로킹) 방식이다.

## Spring WebFlux

> Spring WebFlux는 Asynchronouse(비동기적)으로 동작하는 Non-Blocking(논블로킹) 방식이다.

### Mono & Flux

    - Mono
    - Flux

## 차이점

|                 |     Spring MVC     |                       WebFlux                        |
| :-------------: | :----------------: | :--------------------------------------------------: |
| 데이터 처리방식 |    Synchronous     |                     Asynchronous                     |
|     제어권      |      Blocking      |                     Non-Blocking                     |
|                 |                    | (단, 모든코드가 논블로킹하게 동작해야만 의미가 있다) |
|   Programming   | Imperative(명령형) |                   Reactive(반응형)                   |
|      지원       |     JDBC, JPA      |         반응형 라이브러리 (Reactor, RxJava)          |
