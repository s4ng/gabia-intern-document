## GitLab-Runner를 활용한 CI/CD 설계

### GitLab CI/CD를 선택한 이유
1. 사내에서 GitLab CI/CD를 활용하여 프로젝트를 진행하고 있음.
2. 다른 CI/CD 툴을 사용할 경우 관리해야 할 툴이 늘어나 업무 효율이 떨어질 수 밖에 없고, 비용이 많이 들 수 밖에 없다.

#### CI/CD를 위한 GitLab-Runner 환경
1. Develop PC의 OS가 Windows이므로 Windows GitLab-Runner를 설치 (C:\GitLab-Runner\gitlab-runner.exe)
2. GitLab-Runner executor는 centos 최신버전의 docker images를 pull받아 개발에 맞는 환경 세팅 후 container를 commit함
3. build는 docker image
4. CD는 현재로선 executor docker image의 ssh키를 deploy 서버에 등록하여 ssh접속을 통한 docker 명령 실행 

#### 예정 사항
1. gitlab-ci.yml에 tags 옵션과, only 옵션을 활용해 본인의 역할에 맞는 ci stage 작성
2. checkstyle, pmd, ESlint을 활용한 linter stage 작성