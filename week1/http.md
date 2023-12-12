# 학습 키워드

- HTTP(HyperText Transfer Protocol)
- HTTP와 HTTPS의 차이(TLS)
- 클라이언트-서버 모델
- stateless와 stateful
- HTTP Cookie와 HTTP Session
- HTTP 메시지 구조
  - HTTP 요청(Request)과 응답(Response)
    - multipart/form-data
  - HTTP 요청 메서드(HTTP request methods)
    - 멱등성
  - HTTP 응답 상태 코드(HTTP response status code)
    - 리다이렉션

## 학습 내용

### HTTP(HyperText Transfer Protocol)

HTTP는 HTML 문서와 같은 리소스들을 전송하는 프로토콜, 즉 통신 규약이다.
문서뿐만 아니라 다양한 형태의 데이터들을 전송할 수 있다.

### HTTP와 HTTPS의 차이(TLS)

HTTPS(HyperText Transfer Protocol Secure)는 이름에서도 알 수 있듯이, HTTP에 보안 기능이 추가된 버전이다. HTTPS는 데이터를 전송하기 전에 암호화된 연결을 설정한다.
이를 위해서 HTTPS는 HTTP 요청 및 응답을 SSL 및 TLS 기술에 결합한다.   
SSL은 디지털 인증서로 불리며, 1)인증, 2)암호화, 3)복호화의 SSL 핸드셰이크 과정을 통해 서버와 브라우저 간에 암호화된 연결을 수립한다.
TLS는 SSL의 더욱 향상된 안전한 버전으로, 암호화 외에도 웹사이트 소유자의 신원을 인증하기도 한다.

### 클라이언트-서버 모델

리소스를 사용하는 클라이언트와 리소스가 존재하는 서버를 분리시키는 모델을 말한다.
서버는 클라이언트의 요청을 처리하고 응답한다.

### stateless와 stateful

stateless는 서버가 클라이언트의 상태를 유지하지 않는 것을 의미한다. 그래서 요청을 할 때, 통신에 필요한 모든 상태정보를 클라이언트에서 가지고 있다가 통신할 때 모두 실어 보내야 한다. 서버는 상태를 유지할 필요가 없기 때문에 부하가 많이 줄어든다는 장점이 있다. 하지만 클라이언트에서 모든 데이터를 요청마다 실어 보내기 때문에 더 많은 데이터가 소모된다는 단점이 있다. stateful은 반대로 생각하면 된다.   
http는 stateless한 대표적인 프로토콜이다.

### HTTP Cookie와 HTTP Session

HTTP는 stateless한 프로토콜이기 때문에 각각의 요청이 독립적이다. 즉, 항상 자신이 누구인지 알려줘야 한다. 만약 로그인하고 페이지를 이동할 때마다 로그인이 풀려버린다면 굉장히 불편할 것이다. 이러한 부분을 보완하기 위해 Cookie와 Session이 필요하다.

1. Cookie

- 사용자가 어떤 웹사이트를 방문할 경우, 그 사이트가 사용하고 있는 서버를 통해 사용자의 컴퓨터에 설치되는 작은 정보파일을 말한다.
- 사용자 인증이 유효한 시간을 설정할 수 있다.
- 사용자가 따로 요청하지 않아도 브라우저가 요청 시에 Request Header를 자동으로 넣어 서버에 전송한다.

2. Session

- 일정시간 동안 사용자로부터 들어오는 일련의 요청을 하나의 상태로 보고, 그 상태를 일정하게 유지시키는 기술이다.
- 세션은 쿠키를 기반으로 하지만, 쿠키와 달리 서버에서 관리한다.
- 서버는 클라이언트를 구분하기 위해 세션 id를 부여하고 웹 브라우저가 서버에 접속해서 브라우저를 종료할 때까지 인증상태를 유지한다.

### HTTP 메시지 구조

요청, 응답 메시지 모두 구조는 동일하다. 구조는 아래와 같다.

1.Start line

- 요청이나 응답의 상태를 나타낸다.
- 요청과 응답의 형태가 다르다.

2.Headers

- 요청을 지정하거나, 본문을 설명하는 헤더의 집합이다.

3.Empty line

- 헤더와 본문을 구별하는 빈 줄이다.

4.Body

- 요청, 응답에 관련된 데이터 또는 문서를 포함한다.
- 요청, 응답의 유형에 따라 선택적으로 사용한다.
- 여러 개일 수도 있다. (ex) multipart/form-data

### HTTP 요청 메서드

- GET: 리소스 조회
- POST: 요청 데이터 처리(주로 등록)
- PUT: 리소스 대체(덮어쓰기)
- PATCH: 리소스 부분 변경
- DELETE: 리소스 삭제
- HEAD: GET과 동일하지만, body 제외
- OPTIONS: 대상 리소스에 대한 통신 가능 옵션 설명   

※ 멱등성   
같은 요청을 여러 번 해도 서버의 상태가 바뀌지 않음   
멱등성 메서드: GET, PUT, DELETE, HEAD, OPTIONS

### HTTP 응답 상태코드

- 1XX: 정보
- 2XX: 성공 -> 200 OK, 201 Created, 204 No Content
- 3XX: 리다이렉션 -> 304 Not Modified
- 4XX: 클라이언트 문제 -> 404 Not Found
- 5XX: 서버 문제 -> 500 Internel Server Error
