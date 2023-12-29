# 학습 키워드

- CORS
  - 동일 출처 정책(Same-Origin Policy)
  - JSONP
  - Access-Control-Allow-Origin
- @CrossOrigin

## 학습 내용

### CORS

#### 동일 출처 정책(Same-Origin Policy)

어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 중요한 보안방식이다. 즉, 웹 브라우저 보안을 위해 프로토콜, 호스트, 포트가 동일한 서버로만 ajax요청을 주고 받을 수 있도록 한 정책이다.

#### JSONP

\<script> 태그는 동일 출처를 따지지 않는다는 점을 이용. 서버에서 JSON을 직접 전달하는 게 아니라, 실행되는 자바스크립트 코드를 전달하는 방식이다.   
하지만, JSONP는 여러 보안상의 문제로 인하여 CORS로 대체되고 있다.

#### CORS란?

CORS(Cross-Origin Resource Sharing)를 번역하면 "교차 출처 리소스 공유"이다. 즉, CORS를 설정한다는 것은 출처가 다른 리소스간 공유를 허용한다는 뜻이다.

#### CORS 설정 방법

- 서버에서 Access-Control-Allow-Origin 응답헤더 설정하기
  - ```'Access-Control-Allow-Origin': <origin> | *```

- 프록시 서버 사용
  - 직접적으로 요청하는 것 대신 프록시 서버를 사용하여 리소스로의 요청 전달
  - 리소스와 동일한 출처에서 요청을 보내는 것처럼 만들어 CORS 에러 방지

#### @CrossOrigin

Spring Web에서는 @CrossOrigin 애너테이션을 사용하면 된다. 클래스와 메서드 모두 지정이 가능하다.

```
@CrossOrigin("http://localhost:3000")
```

#### WebMvcConfigurer

WebMvcConfigurer 인터페이스에 대한 Spring Bean으로 환경 설정.

```
@Bean
	public WebMvcConfigurer webMvcConfigurer() {
		return new WebMvcConfigurer() {
		
		@Override
		public void addCorsMappings(CorsRegistry registry) {
			registry.addMapping("/**")
							.allowedMethods("GET", "POST", "PATCH", "DELETE", "OPTIONS")
							.allowedOrigins("http://localhost:3000");
		}
	};
}
```
