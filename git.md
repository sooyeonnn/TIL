# git이란?

: 분산 "버전 관리 프로그램"

#### 의미

1. 버전: 컴퓨터 소프트웨어의 특정상태
2. 관리: 어떤 일의 사무, 시설이나 물건의 유지 개량
3. 프로그램: 컴퓨터에서 실행될 때 특정 작업을 수행하는 일련의 명령어들의 모음

#### 장점

: 코드의 히스토리(버전)을 관리하는 도구로서
  개발되어온 과정 파악 가능, 이전 버전과의 변경사항 비교 및 분석 가능

#### git과 github는 다르다

: git 기반의 저장소 서비스를 제공하는 서버가 github이다.

1. git을 이용한 버전관리
2. github를 이용한 포트폴리오

---

- readme.md: 프로젝트에 대한 설명 문서
- repository: 특정 디렉토리를 버전 관리하는 저장소

#### commit

1. **working directory**: 작업하고 있는 실제 디렉토리  ex) 용돈받음
2. **staging area**: 커밋으로 남기고 싶은 특정 버전으로 관리하고 싶은 파일이 있는 곳 -- 커밋대기소 ex) 지갑
3. **repository**: 커밋이 저장되는곳 ex) 은행

#### file

1. **untracked file**: git이 관리하지 않는 파일
2. **tracked file**: git이 관리하는 파일
3. **staged file**: staging area에 올라간 상태 / staging area: commit을 원하는 파일들이 대기하는 곳
4. **committed file**: commit이 완료된 상태 , repository에 반영된(올라간) 상태

#### 순서도

1. untracked file: git이 관리하지 않는 파일
2. (**git add** 명령어 사용)
3. tracked file로 바뀜 + staging area로 옮겨짐(staged file)
4. (**git commit** 명령어 사용)
5. repository로 이동 (committed file), working directory의 untracked file이 modified file로 변경
   (modified file: git이 관리하며 최신인 상태)

#### 명령어

- **git status** :현재 git으로 관리하고 있는 파일들의 상태 확인 
- **git init**: 로컬 저장소를 생성 / .git 폴더에 readme.md 생성
- **git add 파일 이름**: 추적되지 않은 모든 파일과 추적하고 있는 파일 중 수정된 파일을 모두 staging area에 올림
- **git add . **: 모두 add 함
- **git commit -m "commit_message"**: repository로 이동 (commit_message: 변경의 이유에 대해서 설명)
- **git config -**: 사용자 이름, 이메일 지정
- **git log**: 수정 기록을 볼 수 있음 git log 후 명령어 종료는 q이다 
- **git diff**: 수정된 부분을 알려줌

---

# github란?

#### 인터페이스

: 통신할 때 사용 

1. **CLI(command line interface)**: 명령어를 통해 사용자와 컴퓨터가 상호작용하는 방식
2. **GUI(graphic user interface)**: 그래픽 유저 인터페이스 - 마우스로 조작, 그래픽을 통해 사용자와 컴퓨터가 상호작용하는 방식
- GUI는 CLI에 비해 사용하기 쉽지만 단계가 많고 컴퓨터의 성능을 더 많이 소모, 수많은 서버 / 개발 시스템이 CLI를 통한 조작 환경을 제공한다

#### 명령어

- **touch**: 파일 생성 ex) touch nct.txt
- **mkdir**: 새폴더 생성
- **ls**: 현재작업중인 디렉토리의 폴더 파일 목록을 보여주는 명령어
- **cd**: 현재 작업중인 디렉토리를 변경하는 명령어
- **start, open**: 폴더/파일을 여는 명령어 (윈도우는 start, 맥은 open 사용)
- **rm**: 파일을 삭제하는 명령어 
- **rmdir**: 폴더 삭제하는 명령어

#### git hub와 로컬 repository 연결

(remote add or clone 사용)

1. **remote add**
   git remote add origin https://github.com/sooyeonnn/first
   git push -u origin master or git push -u origin main
   git pull origin master master --allow-unrelated-histories
   : remote repo를 local로 복사합니다

2. **clone**
   바탕화면 명령프롬프트에서 
   git clone https://github.com/sooyeonnn/first.git
   git add .
   git commit -m "test 파일 추가"
   git push
   : local repo의 최신 커밋을 remote repo로 push 합니다.

#### 수정한 뒤 commit 방법

1. git add . 
2. git commit -m "test 파일 추가"
3. git push

---

# 경로

1. 절대경로
   : 루트 디렉토리부터 목적 지점까지 거치는 모든 경로를 전부 작성한것
   /c/Users/multicampus/Desktop/gittest
   pwd - 현재경로 확인하는 명령어

2. 상대경로 
   : 현재 작업하고 있는 디렉토리를 기준으로 계산된 상대적 위치를 작성한 것
   현재 작업하고 있는 디렉토리가 C:/user일때
   윈도우 바탕화면으로의 상대경로는 ssafy/desktop
   ./: 현재 작업하고 있는 폴더
   ../: 현재 작업하고 있는 폴더의 부모 폴더

ctrl + ` : 터미널 열기
우측상단 + git bash 누르면 git bash를 vs code에서 사용가능



--- 

# 최초 등록 시

1. git init -> git remote or UI로 생성 -> git clone

2. 글작성

3. add & commit & push





# 2번째부터

git pull



--- 

# 오류 해결

### pull이 안 될 때

git pull --allow-unrelated-histories

### 저장명령어

:wq



--- 

# branch 통합 방법



![Image Pasted at 2022-7-19 10-06.png](assets/868b5ecb40b98739df3d4193872b248fc1e29fcd.png)
