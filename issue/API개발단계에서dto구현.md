## Backend api에서 entity와 dto를 구분하여 설계해야 하는 이유

- Entity 클래스는 DB 테이블의 속성들과 일치하는 값들을 갖고 있음.
- 그러나 Controller에서 요청과 응답을 Entity 클래스만을(다른 테이블 join을 한 경우 같은) 가지고 결과 값을 줄 수 없는 경우가 빈번함.
- 또한 DB 테이블에는 비지니스 로직을 위한 여러 속성들 중에 외부로 노출되서는 안되는 속성들이 포함.
- entity객체는 **db** layer와 데이터를 주고받을 때 사용되며 **dto**객체는 **View** layer(api -> Json)와 데이터를 주고 받을 때 사용.

##### 따라서 Entity 클래스와 Controller에서 쓸 DTO는 **꼭 분리해서 사용**해야 함


DTO 클래스를 생성 후에 ModelMapper를 적극 활용하면 맵핑하는 반복 작업을 줄일 수 있다.

![DTO설명](/uploads/19a7640fe9737011e05377420f323f41/DTO설명.png)

---
@gm2202969 @gm2202971