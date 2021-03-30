## DB구축 정리 사항       
1. gCloud 서버에 mysql 8.0 docker image를 pull받아 db 구축
2. Workbench를 활용하여 erd 설계를 한 뒤 자동으로 테이블 생성과 sql 쿼리 추출

### MySQL 컨벤션
1. 모든 네이밍은 **소문자**로 한다.
2. 단어가 여러개 이어지는 경우 `_`를 이용해 연결한다 (예: used_board)
3. 모든 단어는 **단수**로 작성한다. (예 : ~~comments~~ comment)
4. **축약어**의 사용은 지양한다.
5. 동사의 경우 **수동태**를 사용한다 (예 : ~~register_date~~ registered_date)

### erd 개요( 2021-01-25 )   
1. 전체 게시글을 나타낼 Board
2. 중고 판매 카테고리를 위한 Used_Item
3. 나눔 카테고리를 위한 Sharing
4. 나눔 추천을 위한 Raffle
5. 유저 활동 점수를 나타내기 위한 User_Activity

![erd_png](uploads/0d3fed4d48ff6dbcfeced1b2bf837a36/erd_png.png)

### 2021-01-27

#### 변경 사항
1. 알림, 공지사항, 이미지 테이블 생성
2. 중고, 나눔 게시판 및 댓글 테이블 분리
3. 관계, 키 정리
4. 정규화(1, 2, 3)

![erd0127](uploads/05aec112f510ee5613d9be88056052a6/erd0127.png)

### 2021-02-02

#### 변경 사항
1. 이미지 테이블 삭제 (디렉토리로 저장하는 방식 따름)
2. 각 테이블 생성, 수정 시간 속성 추가
     - DATETIME 타입 선택 후 디폴트 값으로 생성 시간 자동 설정
     - ON UPDATE CURRENT_TIMESTAMP를 설정하여 수정 시간 자동 설정
3. 글 내용 속성 varchar(1000) -> LONGTEXT로 변경
4. 각 게시판의 status는 INT타입을 선택하고 내부적으로 의미 부여 (1: 생성&진행, 2: 종료, 3: 삭제)

#### 2021-02-03 **추가** 각 게시판 조회수 속성

![erd0202](uploads/014f46761da608e9243a2481477b0bd8/erd0202.png)


### 2021-02-04

![erd0204](uploads/4fa38a22ed6395b24651d28478e1cbf2/erd0204.PNG)