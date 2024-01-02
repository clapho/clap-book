# 학습 키워드

- 직렬화(Serialization)
- 마샬링
- JSON

## 학습 내용

### 직렬화(Serialization)

>데이터 구조나 오브젝트 상태를 동일하거나 다른 컴퓨터 환경에 저장(이를테면 파일이나 메모리 버퍼에서, 또는 네트워크 연결 링크 간 전송)하고, 나중에 재구성할 수 있는 포맷으로 변환하는 과정

객체를 그 자체로 DB에 저장하거나 네트워크로 전송하는 것은 불가능하기 때문에, 객체를 복구할 수 있도록 데이터화 하는 것이 필요하다. 바이너리라면 Byte Stream, 텍스트라면 기계가 파싱할 수 있고 사람도 읽을 수 있는 XML, JSON, YAML등으로 변환한다.

### 마샬링

>컴퓨터 과학에서 마샬링(marshlling)은 한 객체의 메모리에서 표현방식을 저장 또는 전송에 적합한 다른 데이터 형식으로 변환하는 과정이다.

마샬링은 직렬화보다 더 큰 개념으로 사용된다. 직렬화는 객체가 대상이고 마샬링은 변환 그 자체의 목적으로 코드베이스를 기록하는데 차이가 있다.

### JSON

JavaScript Object Notation의 약자로, 데이터를 쉽게 교환하고 저장하기 위한 텍스트 기반의 데이터 교환 표준이다.   
JavaScript의 object는 기본적으로 key-value 쌍이다. Java는 Map이 이와 유사하지만, 스키마 관리 및 타입 안전성을 위해 DTO를 활용한다.

- 생성: DTO(Java 세계) -> 변환기 -> JSON 문자열
- 해석: JSON 문자열 -> 변환기 -> DTO(Java 세계)

Java에선 Jackson이란 도구가 유명하고, Spring Boot에서 Web 의존성을 추가하면 바로 사용할 수 있다.