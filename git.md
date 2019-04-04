# Git == GitHub

-------

- Git = DVCS 버전관리를 하는 프로그램의 일종

- GitHub = SNS의 일종

-----

# Git을 사용하는 이유?

- 충동해결해주고 과거로 롤백해주고 

-----

# 인간의 작업
- 작업디렉토리 (working dir..)
- working tree
- 파일(소스코드) 편집

----------
# Git 

- 커밋 = 게임의 세이브 포인트
- 한번 커밋을 하면 안전하게 저장이 된다.
- 로컬 저장소에 들었다.(.git)  
= 내컴퓨터의 .git  
= 내컴퓨터가 살아있는 동안만 안전하다.

-----

- 커밋: 스테이지의 내용들을 가지고 커밋 객체를 만드는 행동
- 로컬 저장소 - 커밋들이 저장 됩니다.
- 원격 저장소 
- 스테이지 - 커밋을 준비하는 곳
- 작업 디렉토리


===============================
# linux로 git하기

## 새로운 저장소 만들기
- 폴더를 하나 만들고, 그 안에서 git init 명령을 실행하면 새로운 git 저장소가 만들어진다.
- git status 는 현재 git의 상태를 보여준다.

## 저장소 받아오기
- 로컬 저장소를 clone하려면 아래명령을 실행한다.  
git clone /로컬/저장소/경로

- 원격 서버의 저장소를 복제하려면 아래 명령을실행한다.  
git clone 사용자명@호스트:/원격/저장소/경로  
= github주소를 복사하면 된다.

## 작업의 흐름
- 로컬 저장소는 git이 관리하는 세 가지 장소가있다.
1. Working directory : 작업 디렉토리
2. Index, stage : 스테이지, 인덱스
3. HEAD : commit(최종 확정본)을 나타낸다.

---------

## 추가와 확정(commit)
- 변경된 파일은 git add <파일이름> 또는 git add * 으로 스테이지에 추가할 수 있다.
- 변경내용을 확정하려면 git commit -m "이번 확정본에 대한 설명"으로 HEAD에 반영한다.

## 번경 내용 push(발행)하기
- 현재의 변경 내용은 아직 로컬저장소의 HEAD안에 머물고 있다.
- 이 변경 내용을 원격 서버로 올리는 방법은 git push origin master 이다.(다른 가지를 발행하려면 master를 원하는 가지 이름으로 바꾼다.)
- 만약 기존에 있던 원격 저장소를 복제한 것이 아니라면, 원격 서버의 주소를 git에게 알려줘야한다.  
git remote add origin <원격 서버 주소>

## branch(가지) 만들기
- branch는 안전하게 격리된 상태에서 무언가를 만들 때 사용한다.
- 저장소를 새로 만들면 기본으로 master branch가 만들어 진다.
- 여기서 다른 가지를 이용해서 개발을 진행하고, 나중에 개발이 완료되면 master branch로 돌아와 병합하면 된다.

- git checkout -b newbranch = newbranch라는 branch를 만들고 갈아탄다.
- git checkout master = master branch로 돌아온다.
- git branch -d newbranch =  branch를 삭제한다.
- git push origin <branch 이름> = branch를 원격 저장소로 전송한다. (전송하기 전까지는 다른 사람드이 접근할 수 없다.)

## 갱신과 병합(merge)
- git pull : 원격 저장소의 변경 내용이 로컬 작업 디렉토리에 fetch(받아지고), merge(병합)된다.
- git merge <가지 이름> : 다른 branch에 있는 변경된 내용을 현재가지(ex: master branch)에 병합한다.

- conflicts(충돌)이 일어나면 git이 알려주는 파일의 충돌 부분을 여러분이 직접 수정해야한다.
- git add <파일 이름> : 충동을 해결하고 나서 아까의 파일을 병합하기 위해 사용한다.
- git commit -a : 변경된 파일을 검출하여 인덱스에 추가하고, 그것들을 커밋하는 동가을 명령어로 실행할 수 있다.
- git diff <원래 가지> <비교 대상 가지> : 변경 내용을 병합하기 전에, 어떻게 바뀌었는지 비교해 볼 수도 있다.

---------------------------

## tag(꼬리표) 달기
- git log : 특별한 아규먼트 없이 이 명령을 실행하면 저장소의 커밋 히스토리를 시간순으로 보여준다.
- git tag 1.0.0 a11bef06... : a11bef06..... 이 확정본 식별자에 1.0.0이라는 꼬리표를 단다.

## 로컬 변경 내용 되돌리기
- git checkout -- <파일이름> : 실수로 무언가 잘못한 경우, 로컬의 변경 내용을 되돌릴 수 있다.
- git fetch origin, git reset --hard origin/master : 로컬에 있는 모든 변경 내용과 확정본을 포기하고 로컬 master branch가 저 이력을 가리키도록 한다.

------------------

## 유용한 팁
- gitk : git의 내장 GUI
- git config color.ui true : 콘솔에서 git output을 컬러로 출력하기
