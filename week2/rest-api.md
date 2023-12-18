# 학습 키워드

- API(Application Programming Interface)
- 정보은닉(Information Hiding)과 캡슐화(Encapsulation)
- Architecture와 Architecture Style의 차이
- REST(7가지 제약 조건 - 필딩 제약 조건)

## 학습 내용

### API(Application Programming Interface)

컴퓨터나 컴퓨터 프로그램 사이의 연결이다. 일종의 소프트웨어 인터페이스이며, 다른 종류의 소프트웨어에 서비스를 제공한다.

### 정보 은닉(Information Hiding)과 캡슐화 (Encapsulation)

정보 은닉은 객체지향 언어적 요소를 활용하여 활용해서 객체에 대한 구체적인 정보를 노출하지 않도록 하는 기법이다. 자바의 정보 은닉 기법은 대표적으로 1) 업캐스팅, 2) 캡슐화 3) 인터페이스&추상클래스 이렇게 3가지 정도가 있다. 정보 은닉과 캡슐화를 같다고 오해하기 쉬운데 캡슐화는 정보 은닉의 하나의 방법인 것이다.

### Architecture와 Architecture Style의 차이

Architecture는 시스템의 구성요소들 간의 관계와 원칙, 그리고 그들이 이루는 전반적인 구조를 의미한다. Architecture Style은 반복되는 문제의 해결 방식에서 특정한 종류의 요소들이 서로 특정한 관계 속에서 사용되고 있는 것을 말한다.

### REST

>Roy Fielding - “Architectural Styles and the Design of Network-based Software Architectures” (2000)

Representational State Transfer의 약자로, 자원의 표현에 의한 상태 전달을 의미한다.
구체적으로는, HTTP URI를 통해 자원을 명시하고 HTTP Method를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.

제약 조건

1. Starting with the Null Style

2. Client-Server(클라이언트-서버 구조)   
자원을 요청하는 쪽이 Client, 자원이 있는 쪽이 Server가 된다.

3. Stateless(무상태)   
HTTP가 Stateless 하므로 REST 역시 Stateless 하다.

4. Cache(캐시 가능)   
웹 표준 HTTP 프로토콜을 그대로 사용하므로, Cache 기능도 사용 가능하다.

5. Uniform Interface   
전체적인 시스템 아키텍처를 잘 파악할 수 있도록 하기 위한 약속된 Interface, 해당 규약을 사용자들이 지킴으로써 추후에 사용하는 Client를 개발하는 사용자와 Server를 개발하는 사용자 간의 결합도가 낮아질 수 있다(Decoupling).

- 필딩 제약 조건

  - Identification of Resources   
  → URI 등으로 리소스를 식별할 수 있다.

  - Manipulation of Resources through Representation   
  → 메시지를 통해 리소스를 조작한다. 클라이언트의 요청에 어떤 자원에 대한 적절한 표현과 작업을 수행하기 위한 메타데이터를 충분히 갖추고 있다면, 이는 서버 상에서 해당 자원들을 변경, 삭제할 수 있는 충분한 데이터를 갖고 있다는 의미이다.

  - Self-descriptive Messages   
  → 자기 서술적 메시지라는 의미로, 메시지는 자신을 어떻게 처리해야 하는 지에 대한 충분한 정보를 포함해야 한다.

  - Hypermedia as the Engine of Application State(HATEOAS)   
  → 애플리케이션의 상태는 Hyperlink를 이용해 전이되어야한다. (페이지 변경 등)

6. Layerd System   
계층화된 시스템 아키텍쳐를 사용해서 각 구성들 간의 계층을 마음대로 상호작용 할 수 없도록 제한함으로써 Interface를 일원화할 수 있다.

7. Code-On-Demand(optional)   
Client에 보내는 데이터를 바로 실행 가능한 코드를 보내서 이것을 Client에서 실행하는 것을 말한다.
