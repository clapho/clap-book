# 학습 키워드

- Collection Pattern
- CRUD
- CQS

## 학습 내용

### Collection Pattern

여러 리소스를 하나의 그룹으로 묶어서 표현하는 것을 말한다.

예시 - 게시판

- `/posts`: 모든 게시물을 하나의 URL로 표현한다. 일반적으로 복수형을 사용한다.
- `/posts/{id}` 처럼 일반적인 형태로 쓸 수 있다.

특정 게시물에 댓글이 달리는 상황 - 디렉터리 처럼 구성 가능

- `/posts/{post_id}/comments` => Collection
- `/posts/{post_id}/comments/{id}` => Element

특정 게시물을 수정

- `/posts/{post_id}/edit` =>"Edit page"라는 리소스
- REST API의 경우, 페이지만 표현할 일은 거의 없다. 이런 표현은 F/E에 맡기고, `/items`, `items/{id}`와 같은 URL만 쓰도록 제한해도 무방

그룹이 아닌 경우는 단수형도 사용 가능

- `/session`

### CRUD

데이터에 취하는 모든 기능

- Create
- Read
- Update
- Delete

HTTP Method를 이용

- GET -> Read
- POST -> Create
- PUT, PATCH -> Update
- DELETE -> Delete

### CQS

Command Query Seperation의 약자로, Command와 Query를 분리하자는 개념을 말하며, 
Command는 상태를 변경하는 메서드, Query는 상태를 변환하지 않는 메서드를 뜻한다.   
CRUD에서 보면 Create, Update, Delete는 상태를 변환하고, 안전하지 않다는 특징이 있다. 반면에 Read는 상태를 변환하지 않기 때문에 안전하고, 분산, 캐시 등이 수월하다는 특징이 있다.   
CQS 패턴을 사용하면 읽기와 쓰기가 동시에 일어나지 않기 때문에 성능을 최적화 하는데 도움을 줄 수 있다.
