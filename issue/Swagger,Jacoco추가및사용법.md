### Swagger 

- **{url}/v2/api-docs**
  - API docs JSON으로 보기
  - http://139.150.76.155:8080/v2/api-docs
- **{url}/swagger-ui.html**
  - swagger-ui 페이지로 보기
  - http://139.150.76.155:8080/swagger-ui.html

#### 살짝 문제점

![swagger1](/uploads/d31e46e267c14a2bc31b92a17fdd93bd/swagger1.png)

샘플 출력 데이터로 나오는 부분이 `data: {}` 와 같이 빈 객체로 나온다.

Controller 에서 반환값으로 너무 많이 감싸서 이런 문제가 생기는 것 같다.

``` java
//현재 반환 데이터 상황
ResponseEntity : { // 상태코드 및 반환 객체 포함

  ResponseWrapperDto : { // 반환 값을 `data : {}` 와 같이 묶어주는 Dto 객체

    SomeBoardResponseDto : { // Entity에서 Dto로 정제한 실제 반환 값'

      "title" : "~~"
      "description" : "~~~"
      ...

    }
  }
}
```

심각한 기능 상의 문제가 아니므로 문제 해결은 우선순위를 뒤로 미루기로 결정!


### Jacoco

- test 방법 (커맨드 라인)
  - ./gradlew clean test
  - 테스트 자동으로 완료 후 /build/reports/jacoco/ 안에 테스트 커버리지 파일 생성

![testCoverage](/uploads/405160e22b2264af0c20eb2d5cbedf9f/testCoverage.png)

#### https://docs.gitlab.com/ee/ci/pipelines/settings.html#test-coverage-parsing

위 방법을 이용하면 테스트 커버리지를 머지 할 때마다 파싱하여 자동으로 MR에 표시할 수 있다.

<!--
@gm1702846 @GM1802883 @gm1902894

@gm2202969 @gm2202971 @gm2202970 @gm2202978