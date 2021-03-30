## API 설계 규칙
1. URI는 리소스만 식별해야한다.
2. URI에 행위를 포함하지 않는다.
3. HTTP 메서드를 통해서 행위를 구분한다.
4. URI에 `_`를 포함하지 않는다.

## /api (2021-02-04)

| 분류          | METHOD | URI                                | 설명                      |
|-------------|--------|------------------------------------|-------------------------|
| 게시글 - 나눔    | GET    | /boards/share/posts?page=1         | 나눔 게시판 페이지 게시글 조회       |
|             | GET    | /boards/share/posts/{id}           | id의 게시글 조회 (1개)         |
|             | POST   | /boards/share/posts                | 게시글 생성 (응답 : 게시글 id)    |
|             | PUT    | /boards/share/posts/{id}           | id 게시글 수정               |
|             | DELETE | /boards/share/posts/{id}           | id 게시글 삭제               |
| 게시글 - 중고    | GET    | /boards/used/posts?page=1          | 중고 게시판 페이지 게시글 조회       |
|             | GET    | /boards/used/posts/{id}            | id의 게시글 조회 (1개)         |
|             | POST   | /boards/used/posts                 | 게시글 생성 (응답 : 게시글 id)    |
|             | PUT    | /boards/used/posts/{id}            | id 게시글 수정               |
|             | DELETE | /boards/used/posts/{id}            | id 게시글 삭제               |
| 게시글 - 공지    | GET    | /boards/notice/posts?page=1         | 나눔 게시판 페이지 게시글 조회       |
|             | GET    | /boards/notice/posts/{id}           | id의 게시글 조회 (1개)         |
|             | POST   | /boards/notice/posts                | 게시글 생성 (응답 : 게시글 id)    |
|             | PUT    | /boards/notice/posts/{id}           | id 게시글 수정               |
|             | DELETE | /boards/notice/posts/{id}           | id 게시글 삭제               |
| 댓글 - 나눔     | GET    | /boards/share/comments?postid={id} | 나눔 게시판 id 글의 댓글 전부 조회   |
|             | POST   | /boards/share/comments             | 나눔 게시판 댓글 생성 (응답 댓글 id) |
|             | DELETE | /boards/share/comments/{id}        | id 댓글 삭제                |
| 댓글 - 중고     | GET    | /boards/used/comments?postid={id}  | 중고 게시판 id 글의 댓글 전부 조회   |
|             | POST   | /boards/used/comments              | 중고 게시판 댓글 생성 (응답 댓글 id) |
|             | DELETE | /boards/used/comments/{id}         | id 댓글 삭제                |
| 래플          | GET    | /raffles?postid={id}               | id 나눔글에 참여한 raffle 리스트  |
|             | POST   | /raffles                           | 래플 참여자 생성(신청)           |
|             | DELETE | /raffles?post={id}&userid={id}     | 래플 참여 취소(삭제)            |
| 회원          | GET    | /users/{id}                        | id 유저 정보 조회             |
|             | POST   | /users                             | 유저 생성                   |
|             | PUT    | /users/{id}                        | id 유저 정보 수정             |
|             | DELETE | /users/{id}                        | id 유저 정보 삭제             |
| 알림          | GET    | /alerts?userid={id}                | id 유저에게 온 알림 리스트 조회     |
|             | POST   | /alerts                            | 알림 생성                   |
|             | PUT    | /alerts/{id}                       | id 알림 수정 (상태값)          |
|             | DELETE | /alerts/{id}                       | id 알림 삭제                |
| 이미지 (추후 구현) | GET    | /boards/share/images?postid={id}   | 나눔 게시판 id 글의 이미지 조회     |
|             | GET    | /boards/used/images?postid={id}    | 중고 게시판 id 글의 이미지 조회     |
|             | GET    | /images/{id}                       | id 이미지 1개 조회            |
|             | POST   | /images                            | 이미지 생성(저장)              |
|             | DELETE | /images                            | 이미지 삭제                  |
