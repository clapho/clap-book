# 학습 키워드

- Spring AOP(Aspect Oriented Programming)
- Dependency Injection
- 싱글턴 패턴
- IoC(Inversion of Control)
- Spring Bean
- BeanFactory

## 학습 내용

### Spring AOP(Aspect Oriented Programming)

> AOP(Aspect Oriented Programming)는 직역하면 관점 지향 프로그래밍으로, 관점에 따라 핵심로직과 부가기능을 분리하여 모듈화하여 재사용하는 개념을 말한다.

보통 부가 기능(ex 로그 추적 로직)은 여러 클래스에 걸쳐서 사용된다. 이러한 부가 기능은 횡단 관심사(cross-cutting concerns)가 되는데, 이렇게 되면 부가 기능을 적용할 때 많은 반복이 필요하고, 여러 곳에 중복코드를 만들어 낸다.   
AOP는 애플리케이션을 바라보는 관점을 하나하나의 기능에서 횡단 관심사 관점으로 달리 보고, 위와 같은 부가 기능의 문제를 해결한다.   

#### 적용 방식

세 가지 방식이 있다.   

1. 컴파일 시점   
.java 소스코드를 컴파일러를 사용해서 .class를 만드는 시점에 부가 기능 로직을 추가한다. AspectJ가 제공하는 특별한 컴파일러를 사용한다.   
하지만 컴파일 시점에 부가 기능을 적용하려면 특별한 컴파일러도 필요하고 복잡해진다는 단점이 있다.

2. 클래스 로딩 시점   
.class 파일을 JVM에 저장하기 전에 조작해서 부가기능을 적용한다.(로드 타임 위빙)   
이 방법은 자바를 실행할 때 특별한 옵션(java -javaagent)를 통해 클래스로더 조작기를 지정해야 하는데, 이 부분이 번거롭고 운영하기 어렵다.

3. 런타임 시점(프록시)
프록시를 통해 부가 기능을 적용한다. 스프링 AOP는 이 방식을 사용한다.   
프록시를 사용하기 때문에, 스프링 AOP는 메서드 실행 지점에만 AOP를 적용할 수 있다.

&nbsp;

### Dependency Injection

> 객체 간의 의존 관계를 외부에서 결정하고 주입해주는 것을 말한다. 인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않도록 하고, 런타임 시에 관계를 동적으로 주입하여 유연성을 확보하고 결합도를 낮출 수 있게 해준다.

예전에는 Spring 개발자들이 Property주입(Setter Injection)을 많이 사용했지만 최근에는 생성자 주입을 권장한다.

&nbsp;

### 싱글턴 패턴

> 소프트웨어 디자인 패턴에서 **싱글턴 패턴**을 따르는 클래스는, 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다. 이와 같은 디자인 유형을 **싱글턴 패턴**이라고 한다.

#### 구현 방법

인스턴스를 오직 한 개만 만들고 하나의 인스턴스에 글로벌하게 접근할 수 있는 방법을 제공

- private한 생성자로 new 사용 막음
- static한 메서드 제공

&nbsp;

1. 가장 나이브한 방법(스레드세이프x)

```
public class Settings {
	
	private static Settings instance;

	private Settings() {}

	public static Settings getInstance() {
		if(instance == null) {
			instance = new Settings();
		}
		
		return instance;
	}
}
```

&nbsp;

2. synchronized 키워드 사용 (동기화 처리작업 → 성능 불이득)

```
public class Settings {
	
  private static Settings instance;

  private Settings() {}

  public static synchronized Settings getInstance() {
    if(instance == null) {
        instance = new Settings();
    }

    return instance;
  }
}
```

&nbsp;

3. 이른 초기화(eager initialization)   
객체 생성비용이 크다면 성능상 좋지 않을 수 있음

```
public class Settings {
	
  private static final Settings INSTANCE = new Settings();

  private Settings() {}

  public static synchronized Settings getInstance() {
    return INSTANCE;
  }
}
```

&nbsp;

4. double checked locking

```
public class Settings {
	
  private static volatile Settings instance;

  private Settings() {}

  public static synchronized Settings getInstance() {
    if(instance == null) {
      synchronized (Setting.class) {
        if(instance == null) {
          instance = new Settings();
        }
      }
    }

    return instance;
  }
}
```

&nbsp;

5. static inner  클래스 (권장) Lazy   
class loader를 통해 로드될때 synchronized 실행됨   

```
public class Settings {
	
  private Settings() {}

  private static class SettingsHolder {
    private static final Settings INSTANCE = new Settings();
  }

  public static synchronized Settings getInstance() {
    return SettingsHolder.INSTANCE;
  }
}
```

synchronized는 사실은 트랜잭션   
어떤 동작을 하면 그 동작이 중간에 잘리지 않고 한 번에 동작하는 것을 보장   
**그 보장이 가장 잘 되는 곳이 스레드가 클래스를 로딩할 때!**   
스레드가 클래스를 로딩할 때는 아무것도 안하고 그것만 한다.

&nbsp;

### IoC(Inversion of Control)

> 우리 말로 **제어의 역전**이라고 하며, 메소드나 객체의 호출 작업을 개발자가 결정하는 것이 아니라 외부에서 결정되는 것을 의미한다.   
IoC는 프레임워크의 공통적인 특징이라고 할 수 있다.

&nbsp;

### Spring Bean

> 스프링 컨테이너에 의해 생성되고 관리되는 자바 객체

&nbsp;

### BeanFactory

> 빈을 생성하고 의존관계를 설정하는 기능을 담당하는 가장 기본적인 IoC컨테이너이자 클래스를 말한다. 스프링 빈 컨테이너에 접근하기 위한 최상위 인터페이스이다.

#### 특징

- getBean() 제공
- Lazy-loading 방식을 사용: **빈을 사용할 때 빈을 로딩**

#### ApplicationContext

스프링 컨테이너를 이야기할 때, 보통 BeanFactory와 ApplicationContext를 같이 이야기한다.   

특징

- BeanFactory를 확장한 버전
- Eager-loading 방식 사용: **런타임 실행시 모든 빈을 미리 로딩**
- 추가기능
  - MessageSource를 이용한 국제화 기능
  - EnvironmentCapable 환경변수를 이용한 로컬, 개발, 운영 구분
  - ResourceLoader를 이용하여 편리하게 파일, 클래스패스 등의 리소스 조회
  - ...

>BeanFactory라고 말을 할 때는 빈을 생성하고 관계를 설정하는 IoC의 기본 기능에 초점을 맞춘 것이다.   
ApplicationContext라고 말을 할 때는 별도의 정보를 참고해서 빈의 생성, 관계 설정 등의 제어의 총괄에 초점을 맞춘 것이다.

스프링은 특별한 경우가 아니라면 BeanFactory의 모든 기능을 포함하고 추가 기능을 제공하는 ApplicationContext를 사용하기를 권장하고 있다.
