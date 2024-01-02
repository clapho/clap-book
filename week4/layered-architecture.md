# 학습 키워드

- 관심사의 분리
- 응집도
- 결합도
- Layered Architecture
- UUID

## 학습 내용

### 관심사의 분리(Separation of Concern)

관심사란 컴퓨터 프로그램 코드에 영향을 미치는 정보의 집합이다.   
**관심사의 분리**란 관심사에 따라 기능을 나누고 각 기능을 독립적으로 개발한 뒤 이를 조합하는 방식으로 복잡한 소프트웨어를 구성하는 것이다.  관심사의 분리를 실현하기 위해, 캡슐화, 모듈화 등의 방법을 활용한다.   
관심사의 분리를 활용하면, 코드를 이해하기 쉬울뿐만아니라 유지보수에 용이하게 소프트웨어를 만들 수 있다.

### 응집도(Cohesion)와 결합도(Coupling)

일반적으로 좋은 설계는 높은 응집도와 낮은 결합도를 가진다고 말한다.   
그럼 응집도와 결합도는 무엇일까?

#### 응집도

>응집도는 모듈에 포함된 내부 요소들이 하나의 책임/목적을 위해 연결되어있는 연관된 정도이다.

예를 들어, a라는 기능을 수정한다고 할 때, 응집도가 높다면 a 기능이 모여 있는 A 모듈만 찾아서 수정하면 될 것이다. 반대로 응집도가 낮아 a 기능이 흩어져 있다면 수정하기가 쉽지 않을 것이다.
즉, 응집도가 높으면, 변경 대상과 범위가 명확해져서 코드를 수정하기 용이해지는 것이다.   

#### 결합도

>결합도는 다른 모듈과의 의존성의 정도이다.

예를 들어, b라는 기능을 수정하기 위해 b기능이 모여 있는 B 모듈을 수정하는데, 다른 모듈들(A,C,D,..)과 기능이 많이 연관되어 있다면 수정하기 힘들 것이다. 이는 다른 모듈과의 결합도가 높은 상황이라 말할 수 있다.   
결합도는 낮을수록 검토해야 하는 소스의 수가 적어져서 코드를 수정하기가 쉬워진다.

### Layered Architecture

Layered Architecture란 소프트웨어 시스템을 **관심사**별로 여러 개의 계층으로 분리한 아키텍쳐를 말한다.
각 계층은 특정한 역할과 책임이 있고 각자의 역할에만 집중한다. 각 계층은 추상화된 인터페이스로만 소통하며, 소통은 상위 계층에서 하위 계층으로만 이뤄진다.(단방향 의존성)   
Layered Architecture로 코드를 구현하면 코드의 구조를 파악하기 쉬울뿐만아니라 재사용성과 유지보수성이 높아진다.

#### 종류

전통적인 3계층

1. Presentation
2. Domain
3. Data

에릭 에반스의 "DDD"에 나온 4계층

1. UI Layer
2. Application Layer
3. Domain Layer
4. Infrastructure Layer

Layer의 수와 역할은 지정된 것은 아니지만 위의 2가지가 대표적인 Layered Architecture 이다.

### UUID(Universally Unique IDentifier)

네트워크 상에서 고유성이 보장되는 ID를 만들기 위한 표준 규약이다.   

**사용 방법**

```
String id = UUID.randomUUID().toString().replace("-", "");
```

#### ULID(Universally Unique Lexicographically Sortable Identifier)

UUID는 정렬 없이 무작위 값을 생성해내는 반면에, ULID는 사전순으로 정렬이 가능하다.

**사용 방법**

build.gradle에 의존성 추가
```
implementation 'com.github.f4b6a3:ulid-creator:5.1.0'
```

ID 생성
```
String id = UlidCreator.getUlid().toString();
```

#### TSID

위에서 사용한 라이브러리와 동일한 개발자가 ULID를 개선

**사용 방법**

build.gradle에 의존성 추가
```
implementation 'com.github.f4b6a3:tsid-creator:5.2.0'
```

ID 생성
```
String id = TsidCreator.getTsid().toString();
```
