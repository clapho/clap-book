# 학습 키워드

- Jackson ObjectMapper
- ObjectMapper
- @JsonProperty

## 학습 내용

### Jackson ObjectMapper

Jackson의 ObjectMapper를 사용해서 Object -> JSON(문자열), JSON(문자열) -> Object 변환이 가능하다.

#### ObjectMapper 사용법

#### Person 클래스

```
@Getter
@ToString
@AllArgsConstructor
@NoArgsConstructor
public class Person {

    private String name;
    private int age;
    private String address;
}

```

#### 직렬화 및 역직렬화

- Serialization: writeValueAsString 메서드
- Deserialization: readValue 메서드

```
public class ObjectMapperEx {
    public static void main(String[] args) {
        ObjectMapper objectMapper = new ObjectMapper();

        //serialization
        Person person = new Person("zooneon", 25, "seoul");
        String textJson = objectMapper.writeValueAsString(person);

        //deserialization
        Person personObj = objectMapper.readValue(textJson, Person.class);
    }
}
```

### @JsonProperty

Json 형태로 데이터를 주고 받을 때, 서로 파라미터 작성 방식(카멜케이스, 스네이크케이스,..)이 다를 경우 데이터 파싱에 오류가 발생할 수 있다. 이 때 @JsonProperty를 사용하면 key를 매핑시킬 수 있다.
