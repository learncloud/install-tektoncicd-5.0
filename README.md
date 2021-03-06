# Tekton CI/CD Installation Guide

**아래 가이드는 HyperCloud 5.x 버전을 위한 가이드임.**

### Module

| SubModule | Version | Guide |
| ------ | --- | ------ |
| Pipeline | v0.26.0 | [Tekton Pipeline Installation Guide](./README-pipelines.md) |
| Trigger | v0.15.0 | [Tekton Trigger Installation Guide](./README-trigger.md) |
| CI/CD Operator | v0.4.2 | [CI/CD Operator Installation Guide](./README-operator.md) |

### 전체 설치
#### 공통
1. cicd.config 설정
    - imageRegistry: 레지스트리 주소 입력 **(public망으로 구축할때 주석 처리하고 진행)**
    - 각 모듈 버전: 설치할 모듈 버전 (버전 변경 `비추천`)

#### 폐쇄망일 경우
1. 온라인 환경에서 준비
   ```bash
   # cicd.config에 imageRegistry를 주석처리하고 아래 install.sh를 진행
   ./installer.sh prepare-online
   
   ```
   
2. 해당 폴더 (`./yaml`, `./tar` 포함) 폐쇄망 환경으로 복사


3. 실제 폐쇄망 환경에서 준비
   ```bash
   # cicd-ns쪽 tar파일이 없어서 현재는 생성이 안됨. 실제 고객사 들어갈때 or offline으로 생성하고싶으면 해당 이미지파일(.tar)을 docker pull push해야할듯)
   ./installer.sh prepare-offline
   
   ```
   
#### 공통
```bash
# public 환경에서 실행할경우 './installer.sh install'를 바로 실행하면됩니다
./installer.sh install

# private 환경에서 실행할 경우
# 1. cicd쪽 tar 이미지를 docker pull,push합니다
# 2. ./installer.sh prepare-offline'를 실행합니다
# 3. ./installer.sh install를 진행합니다

```

### 전체 삭제
```bash
./installer.sh uninstall

```
