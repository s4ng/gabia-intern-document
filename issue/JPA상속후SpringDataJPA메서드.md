## JPA 상속 사용 후 findById 메서드 사용 시 에러났던 이유 ( 추측 )
- 다른 곳의 코드 오류를 엔티티가 다른 메서드를 사용하여 문제되었다고 착각했던 점
- 또는 컴파일 오류나 코드 상의 문제는 없었으나 데이터베이스에 저장된 기존 값이 잘못되어 조회 되지 않았을 수 있음
- 다양한 연관 관계를 맺은 후 외래키 조건으로 인해 JPA로 drop 되지 않았던 테이블들이 존재함을 확인

## JPA 상속으로 조인 전략 사용 후 findByID 메서드의 sql 쿼리 확인

``` sql
    select
        user0_.user_id as user_id2_13_0_,
        user0_.created_at as created_3_13_0_,
        user0_.modified_at as modified4_13_0_,
        user0_.gabia_id as gabia_id5_13_0_,
        user0_.name as name6_13_0_,
        user0_.password as password7_13_0_,
        user0_.point as point8_13_0_,
        user0_.status as status9_13_0_,
        user0_.user_type as user_typ1_13_0_ 
    from
        user user0_ 
    left outer join
        manager user0_1_ 
            on user0_.user_id=user0_1_.user_id 
    left outer join
        member user0_2_ 
            on user0_.user_id=user0_2_.user_id 
    where
        user0_.user_id=?
```
- 위와 같이 left outer join으로 모든 상속 관계에 있는 자식 엔티티의 식별키와 동일한 값이 있는지 조회하는 쿼리가 작동됨   

- 따라서 JpaRepository<User, Long> 을 상속 받는 레파지토리의 메서드를 활용해도 Member, Manager등 조회 가능됨을 확인