# 학습 키워드

- TCP/IP 통신
- TCP와 UDP
- Socket과 Socket API 구분
- URI와 URL
- 호스트(host)
  - IP 주소
  - Domain name
  - DNS
- 포트(port)
- path(경로)
- Java text blocks
- Java InputStream과 OutputStream
- Java try-with-resource

## 학습 내용

### TCP/IP 통신

>인터넷 프로토콜 스위트(Internet Protocol Suite)는 인터넷에서 컴퓨터들이 서로 정보를 주고받는 데 쓰이는 통신규약의 모음이다. 인터넷 프로토콜 슈트 중 TCP와 IP가 가장 많이 쓰이기 때문에 TCP/IP 프로토콜 슈트라고도 불린다.   
TCP/IP는 패킷 통신 방식의 인터넷 프로콜인 IP와 전송 조절 프로토콜인 TCP로 이루어져 있다. IP는 패킷 전달 여부를 보증하지 않고, 패킷을 보낸 순서와 받는 순서가 다를 수 있다. TCP는 IP 위에서 동작하는 프로토콜로, 데이터의 전달을 보증하고 보낸 순서대로 받게 해준다.

### TCP와 UDP

전송 계층의 대표적인 프로토콜이지만 큰 차이가 있다.
TCP 3-way handshaking 연결, 패킷 교환 방식, 신뢰성 보장, 순서 보장 등의 특징이 있지만, UDP는 비연결형 서비스이고, 데이터그램 방식을 사용한다. 또한 신뢰성, 순서도 보장하지 않는다. TCP에 비해 여러 기능들이 빠져있기 때문에 속도가 빠르다는 장점이 있다.

### Socket과 Socket API

Socket은 네트워크에서 양방향 통신을 할 수 있게 만들어진 연결부, 엔드 포인트이다.   
Socket API는 소켓프로그래밍을 위한 API이다.

### URI와 URL

URI(Uniform Resource Identifier) 인터넷 상의 리소스 자원을 식별하는 고유한 문자열 시퀀스이다.   
URL(Uniform Resource Locator)는 네트워크 상에서 리소스의 "위치"를 나타내기 위한 규악이다.   
URI는 URL의 의미를 포함한다.

### 호스트(host)

호스트는 네크워크에 연결되어 있는 각각의 장치를 의미한다. 호스트는 다른 호스트와 데이터를 주고 받기 위해 자신들을 구분하는 특수한 번호인 IP 주소를 가지고 있다. 하지만 우리가 실제로 사용할 때는 인간이 편리하게 사용하기 위해 IP 주소 자체 보다는 도메인 네임을 이용한다.   
예를 들면 네이버를 접속한다고 할 때, 주소창에 https://www.naver.com 과 같이 입력하여 접속하는 것이다. 이렇게 입력을 하면 DNS 서버에서 도메인 네임을 IP 주소로 변환하여 반환해주고 이를 이용해 네이버에 접속하는 것이다.

### 포트(port)

네트워크 상에서 통신을 할 때, IP 주소를 바탕으로 해당 서버가 있는 컴퓨터에 접근한다. 하지만 하나의 IP에서 여러 프로그램을 실행할 경우, 이를 구분할 방법이 필요하다. 이 때 포트번호를 통해 해당 IP의 특정 프로그램의 서버에 접속할 수 있다.

### Java text blocks

멀티 라인의 문자열을 이스케이프 시퀀스 없이 사용할 수 있는 자바 문법이다.   
예시는 다음과 같다.

```
  String message = """
          GET / HTTP/1.1
          Host: example.com
                          
          """;
```

### Java InputStream과 OutputStream

자바에서 데이터는 Stream을 통해 입출력된다. Stream은 단방향으로 연속적으로 흘러가는 것을 의미한다. 데이터를 입력받을 때는 InputStream, 출력할 때는 OutputStream을 이용한다. 이는 바이트 단위 입출력을 위한 클래스들이고, 문자 단위 입출력을 위해서는 Reader와 Writer 클래스를 이용한다.

### Java try-with-resource

try-catch-finally 문법으로 작성하면 사용 후에 close 메소드를 호출하여 자원을 반납해주어야 한다. 하지만 이는 작업이 번거롭기도 하고 실수로 자원을 반납하지 못하면 문제가 발생할 수 있다. try-with-resource 문법은 자원을 자동으로 반납해주기 때문에 위의 단점들을 방지할 수 있다.
