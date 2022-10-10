### github 기초

#### 리눅스 커맨드라인 기초
 -  pwd :: print working directory
 - ls : List
 - cd : change directory
 - 절대경로는 /로 나타냄 
 - 상위경로는 '..'으로 나타냄
 - 'tab'을 사용하면 경로 자동완성이 됨
 - `list`; 옵션 예) `ls -a, ls -l, ls -al`
 - `mkdir` : make directory
 - `history` : 과거에 쳤던명령어를 알려 줌
 - 123번째 명령어를 복구하고 싶으면 `history 123` 입력 - 

#### VIM 커맨드라인 기초
- 명령모드와 입력모드가 존재함
- vim 에디터를 열때는 명령모드로 진입함
- 명령모드에서는 입력이불가능
- 입력을하려면 입력보드로 바꿔야함 키보드에서 `'i'` 누름
- 입력이 끄나고, 저장하고 나오려면 명령모드로 바꿔야함
 1. 키보드에서 `esc`를 눌러야함
 2. 저장 후 끝내려면 `:wq` 를 입력하면 됩
 3. 파일명을 입력하려면 `:w '파일명'`
 4. 저장 하지않고 끝내려면 `:q!`
 5. 그냥 끝내려면 `:q`
- 위로 스크롤  k git log등에서 내역이 길 때 사용
- 아래로 스크롤 j git log등에서 내역이 길 때 사용
- [참고자료] [링크](https://ssayebee.github.io/wiki/how_to_use_vim.html)

#### vim 비정상종료시 해결방법
- vim이 비정상종료되면 'swp'파일이 생성됨
- ATTENTION 문구가뜨는경우
 1. 두 프로세스, 두 사람이 동시에 한 파일을 수정하는 경우
 2. crash가 나서 vim이 비정상적으로 닫힌 경우
- 기존에 입력했던 내용을 복구하고 싶을때는 `vim -r '파일명'`을 입력하거나 Recovery모드로 진입
- 정상 종료 후, swp 파일 삭제
- `rm 789.txt.swp` <-- `rm` 명령어는 remove 약자

#### 버전관리시스템을 사용하는이유
1.  실행취소, 재실행이 가능함
2.  버전간 소스비교가 가능합
3.  협업이 가능합

#### 커밋
- 변경이 있을때 만듬
- 가능하면 커밋크기가 작을수록 좋음
- 커밋 이력보기
  `git log`

#### 리포지토리
- 정의: 여러파일을 하나로 모은컬렉션
- 리포? 라고 줄임말을 사용한다.
- 일반디렉터리와 디포지터리의 차이 .git

#### Git Bash 최초 세팅하기

- [깃 최초설정](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

  ```python
  - $ git config --global user.name "John Doe"
  - $ git config --global user.email johndoe@example.com
  - $ git config --global core.autocrlftrue
  ```

#### 주요명령어 단축키

 `shift + insert`  // 복사 
 `Ctrl + /` 주석 or 주석해제

#### Repository로 만들기
`git init` (git initialize) : 일반 폴더 → 저장소로 만들기 (.git 숨김폴더 생성됨)

#### Repository 취소
`rm -rf .git` (Remove -Recursive -Force .git) : 저장소로 만든 것 취소 (.git 숨김폴더 삭제)

#### 저장소 상태 파악하기
```
git status
```

#### Git 체크아웃
`git checkout commitID` : 저장소 버전 되돌리기 (+ Git Graph 함께 활용하면 편하게 확인 가능)

이후 `git checkout master`로 처음 상태로 돌아가기

#### Commit 수정
`git rebase -i HEAD~1` : 1개의 최신 커밋을 수정 (edit)

#### 스테이징 영역에 올리기
`git add FileName` : 작업 파일을 스테이징 영역에 추가

#### 스테이징 영역에서 내리기
`git reset FileName` : 파일을 스테이징 영역에서 삭제 (Commit을 작성할 때 포함시키지 않는다.)

#### Commit 작성
`git commit -m "Commit Message"` : Commit 작성

#### Commit 업로드
`git push -u origin main` : 작성한 local branch commits 업로드

#### 브랜치
- 정의 : A branch in Git is simply a lightweight movable pointer to one of these commits.
- 브랜치는 특정한 목표를 가지고 코드를 수정할 때 주로 만듦
  - 이슈 하나당 브랜치 하나를 주로 만듦

#### Git Branch 명령어
1. 브랜치 목록 보기
```
git branch -al
```
2. 브랜치 생성하기
```
git branch BranchName
```
3. 특정 브랜치로 전환하기
```
git checkout BranchName
git switch BranchName
```

#### merge(병합)
- 먼저 최종적으로 병합할 브랜치로 switch(전환) 또는 checkout
```
git switch merge_branch
git merge BranchName  //선택한 브랜치를 가져와 합친다.
git status            //상태보기
git checkout 번호     //특정시점으로 돌아가기
git checkout main     //원래대로 돌아가기
```
#### 자주쓰는 명령어
```
git reset --hard "hash"   /hash 없으면 마지막상태로 돌아감 
git reset --hard
git revert " hash"
git revert --no-commit "hash"
//checkout //git 2.23부터 switch, restore로 분리
git switch -c new-team  //기존 git checkout -b new-team
git branch -d           //브렌치삭제
  ```

#### gitbub 주요명령어

```
  commit  
  branch  
  checkout     // switch, retore로 분리    
  cherry-pick 
  reset 
  revert 
  rebase  
  merge
  pull = fatch + merge
```

#### 실습사이트
[실습 사이트1](https://github.com/Violet-Bora-Lee/git-tutorial)

[실습 사이트2](https://learngitbranching.js.org/)

[실습 사이트3](https://git-school.github.io/visualizing-git/)

#### 몇가지 명령어 사용 예
```
  git reflog 명령어를 사용해 HEAD가 가리키던 커밋 이력을 볼 수 있음
  git checkout main^   //캐럿은 한단계 부모 위치로 이동
  git checkout HEAD~4  //HEAD 4단계 부모로 이동
  git checkout -f main HEAD~3 //main을 강제이동(메인이 아닌 branch에서 사용)
```

#### git에서 과거로 돌아가는 두 방식
```
  reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 지움
  revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행
```

#### Merge 관련
1. base가 같으면 Fast-forword
2. base가 다르면 merge commit을 생성하여 auto merge (conflict는 스스로 처리)
3. github Pull Requeset에서 merge할수있는 3가지 방법: 
```
  create a merge commit
  squash and merge 
  rebase and merge
```
4. merge 옵션 예
```
  git checkout main
  git merge --no-ff feature  //가독성 좋음/
  git checkout main
  git merge --squash feature //하나로 합쳐져서 세세한 구분이 힘듬/
  git commit -m "squash merge message"
```

#### rebase 관련 : /Base를 재 설정 하여 합치는것 /일종의 복사 /깨끝한 커밋/ 
```
  git checkout feature  
  git rebase master //최상단에 복사 붙여넣기, 한줄로 모든 커밋이 저장됨/
  git remote add "branch name" 원격지 주소
  git fetch "branch name" main
  git rebase "branch name"/main
```

#### Cherry-pick : 다른 브랜치에 있는 커밋을 선택적으로 내 브랜치에 적용시키는것/
```
  git checkout main
  git cherry-pick e19c319
  git push origin main
```
: 실제 사용 예
```
  git checkout main
  git checkout -b cherry
  git cherry-pick e19c319(hash)
  git push origin cherry --> githubweb에서 Merge pull request로 main에 merge
  git cherry-pick e19c319(hash) 
```
[강의교재](https://www.yalco.kr/@git-github/4-4/)

[동영상강의](https://www.youtube.com/watch?v=1I3hMwQU6GU)

- 초기셋팅
```
  git config --global user.name
  git config --global user.email
  git config --global core.autocrlf true
  git config --global init.defaultBranch main
  git commit -am "message" add+message //단 신규생성이 아닌 있는 파일경우적용
  git reset --hard dfsdfs(hash) //reset은 이후 생성 로그를 지우고 과거(hash시점)로 되돌리는 것
  git revert fsdfs(hash) //revert는 이후 생성 로그를 지우지 않고 과거(hash시점)을 최후 로그로 되돌리는 것
  git revert --no-commit fsdfs(hash) //commit이 안된상태로 revert
  git swich -c new_branch //checkout > switch, restore로 분리 이전의 `git checkout -b new_branch` 명령과 같음//
  git branch -d 브랜치명  //브랜치명 지우기, 강제삭제(다른브랜치로 적용안된 새로운 커밋이 포함)는 -D 사용
  git branch -m 기존브랜치 새브랜치  //브랜치 이름바꾸기
  git log --all --decorete --oneline --graph //브랜치 내역보기
```

1) merge는 main 브랜치로 이동후 실행
```
  git switch main
  git merge 머지할브랜치명
  
  머지중 중단
  git merge --abort
  git merge --continue //머지중 충돌하면, 충돌 해결 후 add commit 해야함. 
  git add 출돌해결파일
  git commit -m "커밋내용"
  git branch -d 머지브랜치  // 머지한브랜치 삭제
```

2) rebase는 리베이스할 브랜치로 이동후 실행
```
  git switch rebasebranch 리베이스할 브랜치로 이동
  git rebase main //rebasebranch를 main으로 가지이어 붙여 넣기 하여 기존의 가지가 없어짐.
  git switch main // 머지하기위해 main으로 이동
  git merge rebasebranch   아직 HEAD가 이전에 있기 때문에 rebase한곳으로 이동해야함. 
  git branch -d rebasebranch rebase된 브랜치삭제

  리베이스중 중단 시
  git rebase --abort
  git rebase --continue

  리베이스중 충돌하면, 충돌 해결 후
  git rebase --continue 해야하고, 충돌해결후 add commit 해야함. 
  git switch main                 머지하기위해 main으로 이동                    
  git merge 리베이스브랜치명  아직 HEAD가 이전에 있기 때문에 rebase한곳으로 이동해야함.
  git branch -d 리베이스브랜치명
```

#### 공동프로젝트
- main settings에서 Developer settings(Settings / Developer settings) 
- Personal access tokens/ Generate a personal access token을 생성하여 반드시 메모장 등에 복사
- 설정은 우선 repo만 선택
- windows 자격증명관리자에서 github를 찾아 패스워드에 token을 붙여넣기
- 새로운 repository를 만들고 
- repository settings에서 
- collaborators(Manage access)를 클릭하여 팀원을 추가

##### 1) 원격 저장소 사용하기
```
  git remote add origin (원격 저장소 주소) 
  git branch -M main
  git push -u origin main  이후 push하면 자동으로 origin main으로 됨
```
##### 2) push 할 것이 있을 시 pull 하는 두 가지 방법
```
  만일 원격에 누군가가 커밋한 상태있고, 나는 로컬에 커밋할 내용이 있을경우 

  git pull --no-rebase  pull = fatch+merge 이므로 merge 방식
  git pull --rebase      rebase 방식 먼저 메인으로 재배치되어  pull 상의 rebase는 다름 (협업시 사용 OK) pull 방식
  git push               내가 수정한 사항이 수정됨   
  pull 상의 rebase는 다름 (협업시 사용 OK)

  원격지 변경내용산관없이 내로컬의 내용을 강제 푸시 할때(사전에 합의된경우)
  git push --force //주의 일반적으로 사용하지 않음 
```

##### 3) 원격의 브랜치 다루기 
```
  전체(원격,로컬) 브랜치 보기
  git branch --all
  git branch --a
  
  아래 명령어로 원격의 변경사항 확인
  git fetch
  
  아래 명령어로 로컬에 같은 이름의 브랜치를 생성하여 연결하고 switch
  git switch -t origin/from-remote
  git push (원격 이름) --delete (원격의 브랜치명) 원격의 브랜치 삭제
```

##### 4) .ignore 파일내용은 무시할 내용을 적습니다. 
```
  file.c /*파일명 입력*/
  *.c  /*확장자 입력*/
  !not_ignore_this.c /*예외파일-즉 무시하지 않고 포함할 파일*/
  logs /*logs 파일 및 폴더*/
  logs/ /*logs 폴더*/
  logs /*.c /*logs 폴더안의 .c 파일 무시*/
  logs /*debug.log` /*logs 폴더 및 하위폴더의 debug.log파일 무시*/
```

### Branch 병합시 충돌(conflict) 해결법
```
git status
git add FileName
```

`git commit` (Merge 기본 메세지가 있으므로 따로 작성할 필요 없음)

`git log`로 커밋 이력을 출력하여 병합이 제대로 이루어졌는지 확인
Git Branch를 활용한 작업 순서도
master/main 브랜치로 전환

```
git checkout main
git switch main

```

- 원격 저장소의 master/main 브랜치에서 내려받기 (동기화)

```
git pull origin main
```
작업 브랜치 생성
```
git branch BranchName
```
작업 브랜치 변경
`git checkout BranchName`
`git switch BranchName`
소스 코드 수정 후 저장

수정한 파일을 스테이징 영역에 올리기

```
git add FileName
```

commit 만들기
`git commit -m "Commit Message"`

원격 저장소에 브랜치 생성하고 동기화
`git push -u origin BranchName`

Github 사이트에서 Pull Request 생성
`New pull request`

병합 방향 설정
`Create pull request`

1. 로컬 저장소에서 새로운 브런치를 생성하고 이동함(`git checkout -b ~`)
2. 이동한 브랜치에서 원하는 파일 수정 후 저장
3. 저장한 파일을 스테이징하고(`git add ~`), 커밋 생성(`git commit -m "~"`)
4. 3번에서 만든 것을 원격 저장소에 업로드(`git push 브랜치이름 파일이름`)
5. `git push origin 브랜치이름` 으로 브랜치를 원격 저장소에 업로드
6. 원격 저장소에서 'Compare & pull request' 버튼 클릭
7. 'Create pull request' 클릭 후 메모 작성
8. 'Merge pull request'로 원격 저장소 메인브런치 병합 승인 요청
9. 최종권자가 승인('Confirm merge')
10. 원격 저장소 메인브런치에 병합 완료
11. 로컬 저장소에서 main으로 변경 후(`git checkout main`), 변경된 메인을 다시 받음(`git pull origin main`)