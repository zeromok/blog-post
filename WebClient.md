# ***WebClient***
> Spring 5에 추가된 Reactive-stack의 웹 프레임워크  
클라이언트와 서버에서 리액티브 애플리케이션 개발을 위한 논블로킹 Reactive Streams(리액티브 스트림)을 지원  
WebClient는 RestTemplate를 대체하는 HTTP 클라이언트입니다.

## 작성한 계기
  >사내 첫 프로젝트인 정산시스템을 하면서 사내에서 서비스하고있는 서버들에게   데이터를 받아오기 위해(HTTP통신을 하기 위해) WebClient를 사용하기로 했다.  
  맨처음에는 익숙한 RestTemplate를 사용했었는데 다른 팀원분들과의 협의로 WebClient를 사용하기로 결정...!  
  프로젝트를 하며 조금은 익숙해졌지만, 다시한번 공부 및 정리겸 글을 작성하려한다.

## 특징
  - #### 비동기 지원  
    WebClient는 HTTP 요청을 만들기 위한 비동기 메서드를 제공하므로 애플리케이션이 서버의 응답을 기다리는 동안 다른 작업을 계속 실행할 수 있습니다. 이는 성능과 응답성을 향상시키는 데 도움이 될 수 있습니다.
    
  - #### 교차 플랫폼 지원  
    WebClient는 Windows, macOS, Linux 및 iOS 및 Android와 같은 모바일 플랫폼을 포함한 다양한 플랫폼 및 운영 체제와 호환됩니다.

  - #### 프로토콜 지원  
    WebClient는 HTTP, HTTPS, FTP 및 파일 전송을 포함한 다양한 프로토콜을 지원합니다. 이를 통해 원격 서버에서 파일에 쉽게 액세스하고 다운로드할 수 있습니다.

  - #### 사용자 지정 설정  
    WebClient는 제한 시간, 인증 방법, 프록시 서버 구성, SSL/TLS 설정 등을 포함하여 다양한 사용자 지정 가능한 설정을 제공합니다. 이를 통해 특정 요구 사항과 요구 사항을 충족하도록 WebClient를 미세 조정할 수 있습니다.

  - #### 대용량 파일 지원
    WebClient는 큰 파일을 더 작은 조각으로 나누어 전송하는 청크 분할 전송 인코딩을 사용하여 대용량 파일을 효율적으로 처리할 수 있습니다. 이는 메모리 문제를 방지하고 성능을 향상시키는 데 도움이 됩니다.

  - #### 동시 연결  
    WebClient는 여러 동시 연결을 지원하여 애플리케이션이 동시에 여러 요청을 할 수 있도록 합니다. 이를 통해 성능을 개선하고 대기 시간을 줄일 수 있습니다.

## 그래서 어떻게 사용해?
  - WebClient.create() 사용
    > 오버로드된 메서드이며 선택적으로 요청에 대한 기본 URL 설정
  ```java
  import java.io.IOException;
  import org.springframework.web.reactive.function.client.WebClient;

  public class Example {
      public static void main(String[] args) throws IOException {

          String url = "https://www.example.com/";

          String response = WebClient.create()
                                  .get()
                                  .uri(url)
                                  .retrieve() // 응답 받을 때 사용하는 메서드 / body를 받아 디코딩 || exchange() : ClientResponse를 상태값 그리고 헤더와 함께 가져오는 메소드
                                  .bodyToMono(String.class) // 가져온 body를 Mono 객체로 바꿔준다. / Mono : 0 ~ 1개의 데이터 전달
                                  .block();

          System.out.println(response);
      }
  }
  ```  

  - WebClient.Builder API 사용
    > DefaultWebClientBuilder 클래스를 사용하여 클라이언트를 설정  
    아래 예처럼 base를 설정하고 다른 객체에서 사용할 수 있다.

  ```java
    String url = "https://www.example.com/";

    WebClient webClient = WebClient.bilder()
                              .baseUrl(url)
                              .defaultCookie("cookie-name", "cookie-value")
                              .defaultHeader(HttpHeaders.AUTHORIZATION, "Bearer " + "...")
      
  ```

  - 위에서 설정해준 base를 사용하는 법

  ```java
    webClient.get()
            .uri(UriBuilder -> UriBuilder.path("/.../...").queryParam("key", value).build())
            .retrieve()
            .toEntity()
            .build(exampleDTO.class)
            .block();
  ```

## Note
- 2023-03-09 첫 발행
  > 정산 시스템을 하며 현재회사에서 서비스하고있는 서비스서버들과에 API를 통신을 위해 사용한 WebClient를 정리해보았다.  
  다음기회에 더 깊게 공부해봐야겠다.

