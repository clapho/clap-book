# 학습 키워드

- DTO(Data Transfer Object)
  - 프로세스 간 통신(IPC, Inter-Process Communication)
- "무기력한 도메인 모델" 이란 그리고 안티 패턴인 이유
- 자바빈즈(JavaBeans)
- EJB(Enterprise JavaBeans)
- Java의 record
- DAO
- ORM

## 학습 내용

### DTO(Data Transfer Object)

프로세스 간에 데이터를 전달하는 객체를 의미한다.   
데이터 전송이 목적인 객체이기 때문에, 안에 비즈니스 로직 같은 복잡한 코드는 없고 순수하게 전달하고 싶은 데이터만 담겨 있다.

#### IPC   
프로세스간 통신, 즉, 프로세스들끼리 서로 데이터를 주고받는 행위 또는 그에 대한 방법을 말한다.
IPC에서 쓸 수 있는 기술로는 File, Socket 등이 있다.   
Java에선 RPC(SOAP의 일반적인 활용)를 위해 RMI(Remote Method Invocation)란 기술을 제공한다.

#### Tier간 통신

- F/E와 B/E 사이
  - DTO 자체를 그대로 전송할 수는 없고, 직렬화(마샬링)를 통해야 함
  - 직렬화 기술: XML, JSON

- B/E와 DB 사이
  - 옛날에는 Value Object를 DTO란 의미로 사용, Transfer Object로 정정
  - JPA를 지양하고 DDD를 따르는 사람 중 일부는 ORM은 Active Record + DTO처럼 접근

### "무기력한 도메인 모델" 이란 그리고 안티 패턴인 이유

"무기력한 도메인 모델"이란 도메인 객체들에 비즈니스 로직이 거의 없거나 아예 없는 소프트웨어 도메인 모델의 이용이다.

#### 문제점

1. 객체지향의 특성과 장점을 제대로 활용할 수 없음   
  상태는 있지만 행위가 외부에 있음

2. 코드 재사용의 어려움   
  도메인 로직이 서비스 계층에 분산되어 있으면, 비슷한 로직이 여러 서비스에서 중복될 수 있음
  
3. 도메인 로직의 변경이 어려움 
  서비스 계층에 비즈니스 로직이 집중되면, 로직의 변경이나 확장이 어려울 수 있음

### 자바빈즈(JavaBeans)

자바로 작성된 소프트웨어 컴포넌트이다.

#### 자바빈즈의 관례

- 클래스는 직렬화 되어야 한다.
- 클래스는 기본 생성자를 가지고 있어야 한다.
- 클래스의 속성들은 get, set 혹은 표준 명명법을 따르는 메서드들을 사용해 접근할 수 있어야 한다.
- 클래스는 필요한 이벤트 처리 메서드들을 포함하고 있어야 한다.

### EJB(Enterprise JavaBeans)

기업환경의 시스템을 구현하기 위한 서버측 컴포넌트 모델이다. 즉, EJB는 애플리케이션의 업무 로직을 가지고 있는 서버 애플리케이션이다. EJB 사양은 Java EE의 자바 API중 하나로, 주로 웹 시스템에서 JSP는 화면 로직을 처리하고, EJB는 업무 로직을 처리하는 역할을 한다.

### Java의 record

불변(immutable) 데이터 객체를 쉽게 생성할 수 있도록 하는 새로운 유형의 클래스

#### 기존의 불변 데이터 객체

```
public class Person {
    private final String name;
    private final int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }

    public void setName(name) {
        this.name = name;
    }
    
    public void setAge(age) {
        this.age = age;
    }
}
```

보일러 플레이트 코드가 상당히 많은 것을 알 수 있다. Java record를 이용하면 이를 해결할 수 있다.

#### 레코드를 이용한 불변 객체

```
public record Person(String name, int age) {
}
```

위와 같이 Java record를 이용하면 훨씬 간결하게 작성할 수 있다.

### DAO

Data Access Object의 약자로, Database에 접근하는 역할을 하는 객체를 말한다.
DAO는 비즈니스 로직을 분리하여 도메인 로직으로부터 DB와 관련한 메커니즘을 숨기기 위해 사용한다.

### ORM

Object Relational Mapping의 약자로, 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑해주는 것을 말한다.
Java는 클래스를 사용하고, RDB는 테이블을 사용하는데, ORM은 객체 간의 관계를 바탕으로 SQL을 자동으로 생성하여 이러한 불일치를 해결해준다.
