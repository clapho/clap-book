# 학습 키워드

- Java ServerSocket
- Blocking vs Non-Blocking

## 학습 내용

### Java ServerSocket

Java의 ServerSocket 클래스는 서버 프로그램을 구현하는데 사용된다. 구현 순서는 다음과 같다.   

1. 서버 소켓 생성 및 포트 바인딩
2. 클라이언트로부터의 연결을 기다리고 요청이 오면 수락
3. 클라이언트 소켓에서 가져온 InputStream을 읽음
4. 응답이 있다면 OutputStream을 통해 클라이언트에 데이터를 전송
5. 연결 종료
6. 서버 종료

### Blocking vs Non-Blocking

주로 IO의 읽기, 쓰기에서 사용된다.   
Blocking은 작업이 수행되는 동안, 다른 작업은 진행하지 못하고 대기해야 하는 방식이다. 작업이 순차적으로 이루어지기 때문에 이해하기 쉬운 장점은 있지만, 리소스를 효율적으로 이용하지 못하는 단점이 있다.   
반면 Non-Blocking은 작업이 수행중이더라도, 다른 작업을 수행시키는 것이 가능한 방식을 말한다. 이는 리소스를 효율적으로 사용할 수 있다는 장점이 있지만, 작업 흐름이 복잡해지는 단점이 있다.
