#### 해당 글은 GitLab Korea의 강의를 토대로 작성한 글입니다. 
**강의 링크: https://www.youtube.com/watch?v=OAoEJdfCFQM**

IT 업계의 화두는 [ **추상화 - 가상화 - 자동화** ]   
어떻게 우리의 소프트웨어를 더 빨리, 더 안전하게, 더 좋은 내용으로 고객들한테 전달할 수 있을까

이 배경에서 생각해보면, 퍼블릭 클라우드에서 지원하는 여러가지 하드웨어 관련 API들,   
그리고 쿠버네티스에서 할 수 있는 아주 높은 수준의 추상화,   
그리고 GitLab에서 지원하고 있는 CI/CD는 Devops문화를 통해서   
더 빨리 우리가 목표하고 있는 시장에 우리의 제품을( 소프트웨어) 전달할 수 있는가   

GitLab: **Cloud Native** 지원 도구   
1. DevOps 를 통한 서비스 개선 속도 향상 - 직접적으로 지원   
2. CI-CD 를 통한 부서간 업무 속도 향상 - 직접적으로 지원   
3. 마이크로서비스를 통한 서비스 안정성과 확장성 증대 - 간접적으로 지원   
4. 컨테이너를 통한 IT 유연성 증대   

GitLab 말고도 gitHub, jira, open shift 등 사용해서 위처럼 DevOps 시스템을 구축 할 수 있지만   
많은 도구를 사용할 수록 업무 효율이 떨어질 수 밖에 없고, 비용이 많이 들 수 밖에 없다.   
따라서 GitLab 단일 도구를 사용하여 비용 절감과 업무 효율 증대를 노리자!   

git flow 이런 것도 많이 있지만   
GitLab만의 GitLab flow 나름대로의 개발 절차, 개발 방식이라는 것을 가지고 있다.

#### GitLab flow
1. Create an issue - 먼저 이슈를 하나 만든다   
2. Create a merge request - 그 다음 머지 리퀘스트를 하나 만들고   
(Commit your changes) 개발자가 그 코드를 가지고 수정하고   
3. CI pipeline runs - 그 다음 실질적으로 1차적인 CI CD   
4. Review app   
5. Peer review & discussion - 동료 리뷰와 의견   
6. Approve changes - 승인   
7. Merge, issue closed   
8. CD pipeline runs   
9. Monitor your app   

#### 데모 시나리오   
1. 전체적인 메뉴 구성 및 화면 설명   
2. 버그 수정 요청(이슈) 접수 및 담당자 할당   
3. 버그 수정을 위한 MR(Merge Request) 생성 및 담당자 배정   
4. WebIDE를 통한 소스 수정 및 커밋 수행   
5. 개발 브랜치에 커밋된 소스에 대한 빌드/검증/배포 수행   
- 이슈 대시보드   
- 로드맵을 통한 일정 관리 보드 제공   
6. 검증 과정에서 정적 분석이 수행되고 잠재 결함이 수정된 것을 확인   
- 보안 대시보드 확인 (프로젝트 별)   
- 보안 대시보드 트렌드 확인 (그룹 별)   
7. 승인 권자의 다양한 분석 및 검증 내용을 확인하고 코멘트를 달아서 재작업을 지시 하거나 승인을 진행   
7.1 승인권자는 정적 분석 및 취약점 검사 결과를 확인   
7.2 승인권자는 오픈소스 사용 현황을 확인하고 인지한 상태에서 승인을 진행   
8. 마스터 브랜치로 머지를 수행하면서 클라우드 운영 환경으로 배포   
- 배포 대시보드를 통해서 현재 배포 현환을 공유   
-배포 환견별로 현재 어떠한 배포가 이루어지고 있는지 확인   
9. Canary 배포가 이루어 지고, 1차 배포를 수행하고 정상적으로 배포  것을 확인   
10. 이에 따라서 나머지 시스템에 배포를 수행하고 배포된 웹사이트 확인   

![편집](uploads/e912afbeaa5b38674da6b14b2d1faef0/편집.PNG)

1. **Issue** 이슈라는 것은 여러가지 목적으로 사용할 수 있다   
* 결함
* 소프트웨어 버그
* 프로블럼 레포트 
* 기능 보완 요청
* requirement (요구사항을 정의하고 요구사항하고 이슈하고 연결된다거나)
* 웹 인터페이스 이지만 숏컷(단축키)를 쓸 수 있다
* 키보드에서 g+i ->issue 메뉴로 넘어간다  / 키보드에서 g+b -> 보드 메뉴로 넘어간다

issu 생성 기본 틀(템플릿) (가이드 라인)   
예시)   
타이틀:   
상세 설명:   
담당자:   
기한:   

**issue** 라는 것은 시작점, 스타트 포인트라고 보면 된다.   
실제적으로 이슈가 만들어졌는데,   
그 이슈가 정말 소프트웨어를 변경해야 될 이슈 일 수도 있고,   
단순 사용자의 착오라던지, 여러가지 이유가 있을 수 있음   

또한 이슈가 만들어지고 난 다음에 문제를 해결하기 위해 담당자를 할당 할 수도 있고   
아니면 팀 리더라던지, 해당 이슈와 관련된 담당자가 보시고 바로 클로즈 할 수도 있다   

오른 쪽에 메뉴에 중요한 정보를 또 볼 수 있는데,   
이 이슈가 어느 에픽하고 연관이 되어 있는지,   
**Time tracking**은 이 이슈를 처리하기 위해서 내가 몇 시간을 썼다, 아니면 **몇 시간 정도 걸릴거다**   
**Due Date**는 **언제까지 종료하겠다**   

2. 이슈가 생성된 내용을 확인하고 소스 수정을 위해서 "Merge Request"를 생성   
Create Merge Request 버튼을 눌러서 실제적으로 브랜치 만들어 지면서   
소스 코드가 변경 작업이 이뤄지게 됩니다. 
머지 요청에 대한 내용을 확인하고 담당자를 할당 하거나 필요한 코멘트를 추가   

eclipse , vscode, intellij에서 gitlab 서버를 연결해서 IDE를 활용한 소스코드 변경을 할 수 있지만   
GitLab에서도 IDE환경을 제공한다!!! 게다가 버튼 클릭 하나로 즉시 commit 도 가능함   
gitlab runner 설치 : https://assu10.github.io/dev/2020/10/08/gitlab-runner-1/gi   

#### gitlab CI/CD pipeline 구성   
# 수동 배포 설정   
# 수동 job 실행 시 변수 설정   
# CI/CD 파이프라인 그룹화   
# 파이프라인 아키텍처   
→ 파이프라인 아키텍처 - Basic   
→ 파이프라인 아키텍처 - DAG (Directed Acyclic Graph)   
→ 파이프라인 아키텍처 - Child/Parent Pipelines   
# 효율적인 파이프라인 구성   
# 파이프라인 스케쥴링   
# Artifact 사이즈   

itlab ci/cd pipeline 식공 문서: :   
https://docs.gitlab.com/ee/ci/pipelines/index.html   
gitlab ci yml 파일 공식 문서:    
https://docs.gitlab.com/ee/ci/environments/index.html#configuring-manual-deployments   

#### .gitlab-ci.yml 작성법   
# 파이프라인은 Jobs 과 Stages 로 구성된다.   
→  Jobs: 수행할 작업을 정의 예를 들면 코드를 컴파일 하거나 테스트하는 작업   
→ Stages: jobs 를 실행할 시기를 정의   
# Jobs 는 Runner 에 의해 실행되는데 같은 Stage 내의 여러 개의 Jobs 가 병렬로 실행된다.   
# 하나의 Stage 가 성공적으로 종료되면 파이프라인은 다음 Stage 로 넘어가고,   
   만약 Stage 안의 Job 이 실패하면 다음 Stage 는 실행되지 않고 파이프라인이 종료된다.   
# 일반적으로 파이프라인 아래 순서로 실행되는 4개의 Stage 로 구성된다.   
→ build stage - 컴파일 job   
→ test stage   
→ staging stage - deploy-to-stage   
→ production stage - deploy-to-prod   
# 파이프 라인과 구성 job 과 stage 는 각 프로젝트의 CI/CD 파이프라인 구성 파일인    
   .gitlab-ci.yml 에 정의된다.   


