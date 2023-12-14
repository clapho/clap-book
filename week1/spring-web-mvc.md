# 학습 키워드

- Spring
- Spring Boot
- Spring initializer
- Web Server와 Web Application Server(WAS)
  - Tomcat
- Model-View-Controller(MVC) 아키텍쳐 패턴
- 관심사의 분리(Seperation of Concern)
- Spring MVC
- Java Annotation
- Spring Annotation
  - @RestController
    - @Controller
    - @ResponseBody
  - @GetMapping
    - @RequestMapping

## 학습 내용

### Spring

엔터프라이즈용 Java 애플리케이션 개발을 편하게 할 수 있게 해주는 오픈소스 경량급 애플리케이션 프레임워크

### Spring Boot

스프링으로 애플리케이션을 만들 때, 필요한 설정을 간편하게 처리해주는 별도의 프레임워크

### Spring initializer

스프링부트를 기반으로 Spring 관련 프로젝트를 간단하게 설정하고 생성할 수 있도록 도와주는 웹 도구

### Web Server와 Web Application Server(WAS)

Web Server는 HTTP 기반으로 동작하며, 정적 리소스 제공 및 기타 부가기능이 있는 서버이다. 예시로 NGINX, APACHE 등이 있다.   
WAS는 웹서버 기능을 포함하며, 프로그램 코드를 실행해서 애플리케이션 로직을 수행한다. 예시로는 Tomcat, Jetty, Undertow 등이 있다.   
하지만 웹 서버도 프로그램을 실행하는 기능을 포함하기도 하고, WAS도 웹서버의 기능을 제공하기 때문에 둘의 용어 경계가 모호하다. WAS가 애플리케이션 코드를 실행하는데 더 특화되어 있다고 이해하면 좋을 것 같다.

### Model-View-Controller 아키텍쳐 패턴

프로젝트를 구성할 때 그 구성요소를 Model, View, Controller 세가지의 역할로 구분한 패턴이다.

- Model: View에 출력할 데이터를 담아둔다.
- View: Model에 담겨있는 데이터를 사용해서 화면을 그린다.
- Controller: HTTP 요청을 받아서 파라미터를 검증하고, 비즈니스 로직을 실행한다. 그리고 뷰에 전달할 결과 데이터를 조회해서 모델에 담는다.

### 관심사의 분리(Seperation of Concern)

소프트웨어 개발에서 가장 기본적인 원칙 중 하나이다.   
프로그램을 하나의 단일 블록으로 작성하지 않고, 작은 조각으로 나누어 각각의 간단한 개별 작업을 완료할 수 있도록 만드는 것이다.   
MVC가 추구하는 것은 UI와 비즈니스 로직의 분리이다.

### Spring MVC

Spring MVC는 Map과 유사한 Model 인터페이스를 제공한다. 애플리케이션 전체가 아니라, 웹과 관련된 부분에서만 MVC 개념을 활용할 수 있도록 도움을 줘서 관심사의 분리를 더 심화할 기회를 제공한다.

### Java Annotation

자바 소스코드에 추가하여 사용할 수 있는 메타데이터의 일종이다. @ 기호를 앞에 붙여서 사용하고 JDK 1.5 이상의 버전에서 사용 가능하다.   

어노테이션의 용도

- 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보 제공
- 소프트웨어 개발 환경이 빌드나 배포시 코드를 자동으로 생성할 수 있도록 정보 제공
- 런타임에 특정 기능을 실행하도록 정보 제공

### Spring Annotation

- @RestController
  - @Controller
  - @ResponseBody
- @GetMapping
  - @RequestMapping