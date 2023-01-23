# ***WebClient***
> WebClient는 RestTemplate를 대체하는 HTTP 클라이언트입니다.
- - - 

기존의 동기 API를 제공할 뿐만 아니라, 논블로킹 및 비동기 접근 방식을 지원해서 효율적인 통신이 가능합니다.

WebClient는 요청을 나타내고 전송하게 해주는 빌더 방식의 인터페이스를 사용하며,
외부 API로 요청을 할 때 리액티브 타입의 전송과 수신을 합니다. (Mono, Flux)



WebClient은 아래와 같은 특징을 정리하면 아래와 같습니다.
- 싱글 스레드 방식을 사용

- Non-Blocking 방식을 사용

- JSON, XML을 쉽게 응답받는다.

## Create() & builder()
 ### - create()

```
WebClient.create(); || WebClient.create("baseURL");
```

### - builder()


```
Webclient.builder()
    .baseUrl()
    .defaultCookie("cookieKey", "cookieValue")
    .defaultHeader(HttpHeaders.CONTENT_TYPE, MediaType.APPLICATION_JSON_VALUE)
    .defaultUriVariables(Collections.singletonMap("url", "http://localhost:8080"))
    .build();
```

Request
---


Response
----
### retrieve() : body를 받아 디코딩하는 간단한 메소드
   - toEntity()
     - status, headers, body를 포함하는 ResponseEntity타입으로 받을 수 있음
     - toMono(), toFlux()
       - body의 데이터만 받고싶다면 사용


### ~~exchange()~~ : *deprecated*, exchangeToXXX() 메소드를 사용하자.


### Mono<>, Flux<>
   - 응답으로 받은 Mono, Flux 타입은 어떻게 사용할까?
   
           // blocking
           Mono<Employee> employeeMono = webClient.get(). ...
           employeeMono.block()

           // non-blocking
           Mono<Employee> employeeFlux = webClient.get(). ...
           employeeFlux.subscribe(employee -> { ... });


Configuration
---





참고
- - -
[Spring WebClient, 어렵지 않게 사용하기](https://gngsn.tistory.com/154)




