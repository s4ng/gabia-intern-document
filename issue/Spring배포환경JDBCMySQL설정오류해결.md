현재 배포 환경의 운영 상황

| Pablo's gCloud  | Dino's gCloud |
|--------|------|
| MySQL (DB)   | web(Front-end)     |
| API (Server) | |

이 상태에서 API 서버가 MySQL에 접속하기 위해서는 localHost의 3306 포트로 접속해야 함이 명백하다.

하지만 현재 설정 상황
```yml
spring:
  datasource: #database source 작성
    url: jdbc:mysql://139.150.76.155:3306/gmarket?characterEncoding=UTF-8 # 쿼리 스트링으로 UTF-8 인코딩 설정
    username: root
    passowrd:
    driver-class-name: com.mysql.cj.jdbc.Driver

```
개발 환경에서 접속하기 위해서는 gCloud의 IP에 접근해야 하기 때문에 저렇게 설정하였다.

빌드 후 운영환경에 배포할 때에는 spring.datasource.url 의 ip부분을 localhost로 넣어야 정상적으로 작동한다.

배포 : http://139.150.76.155:8080/

### 테스트 실패로 빌드 실패하는 경우

./gradlew clean build -x test

<!--

@gm1702846 @GM1802883 @gm1902894 

@gm2202970 @gm2202978 @gm2202971 @gm2202969