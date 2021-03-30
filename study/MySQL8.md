### Mysql 최신 버전(8)을 선택한 이유   
1. 현재 제공된 개발 환경에서 Mysql 최신 버전을 사용하는데 큰 문제가 없음
2. 폐쇄된 환경에서 작은 팀 프로젝트를 진행하기 때문에 최신 버전을 활용해보는 것이 더 좋은 경험이 될 것이라 판단.


#### 5버전에서 8버전으로 변경되면서 어떤 이점 생겼는지 정리
 
- NoSQL Document Store는 개발자가 기존 SQL 관계형 응용 프로그램과 **NoSQL, 스키마 없는 문서 데이터베이스 응용 프로그램을 개발할 수 있는 유연성을 제공**. 따라서 별도의 NoSQL 문서 데이터베이스가 필요하지 않음.   
- SQL WINDOW 함수, Common Table, NOWAIT 및 SKIP LOCKED, 내림차순 인덱스, Grouping, 정규식, Character Sets, Cost Model 및 히스토그램.   
- JSON Extended 구문, 새로운 기능, 향상된 정렬 및 부분 업데이트. JSON TABLE 함수를 사용하면 **JSON 데이터 용 SQL machinery를 사용할 수 있음.**   
- GIS Geography 지원. Spatial Reference Systems(SRS)뿐만 아니라 SRS aware spatial 데이터 유형, spatial 인덱스 및 spatial 함수 등이 있음.   
- Reliability DDL 문은 원자성 및 충돌 안전성이 있으며 meta-data는 트랜잭션 데이터 사전에 싱글 저장.   
- Observability Performance Schema, Information Schema, Invisible Indexes, Error Logging.   
- Manageability Persistent Configuration 변수, Undo tablespace 관리, Restart 명령어 및 새로운 DDL.   
- High Availability InnoDB Cluster는 데이터베이스에 통합 된 네이티브 HA 솔루션을 제공.   
- Security OpenSSL 개선, 새로운 기본 인증, SQL Roles, breaking up the super privilege, 암호 강화, 권한 부여.  
- Performance는 MySQL 5.7보다 최대 **2배 빠른 속도**.   
 
MySQL 8.0은 SQL, JSON 및 GIS와 같은 분야에서 개발자가 요청한 많은 새로운 기능을 제공함.   
개발자는 Emojis를 저장할 수 있기를 원하므로 UTF8MB4가 이제 8.0의 default character set가 됨


참고한 링크: https://www.codetd.com/ko/article/6808446