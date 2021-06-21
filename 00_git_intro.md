# Git 초기 설정

**커밋(버전) 작성자(author) 설정**

- 최초 1회 설정
- commit을 누가 작성했는지 알 수 있게 설정해야 한다. 
- 이는 인증(로그인)과는 전혀 관계없음

```bash
$ git config --global user.name "justin kim"
$ git config --global user.email "edujustin.hphk@gmail.com" # github에 가입한 이메일과 동일해야 한다. 
```



설정값 확인

```bash
$ git config --global --list
user.name=justin kim
user.email=edujustin.hphk@gmail.com

```



**커밋 편집기 변경**

- 기본 텍스트 편집기인 `vim`을 `vs code`로 대체하는 것
- 이 설정을 하기 위해서는 vs code가 반드시 설치되어 있어야 한다.

```bash
$ git config --global core.editor "code --wait"
```



## Git basic

### 로컬 저장소 설정

- `(master)`라고 하는 표시(?)가 붙는다. 

```bash
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/git_practice/.git/
```



- 폴더에 git 저장소를 초기화 하면 `.git`이라는 폴더가 생긴다. (숨긴 폴더)

```bash
$ ls -a
./  ../  .git/  a.txt  b.txt
```

![Screen Shot 2021-06-21 at 오후 3.38](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%203.38.png)



## add

- Staging Area(INDEX)로 옮기는 작업
- commit(버전으로 확정)하기 전에 머무는 곳

```bash
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        a.txt
        b.txt

nothing added to commit but untracked files present (use "git add" to track)
```



```bash
$ git add a.txt # a.txt를 WD -> SA로 옮긴다. (commit하기 위한 대기를 하는 곳)

$ git status
On branch master

No commits yet

# commit을 하기 위한 변경 사항들
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt

# 아직 트래킹되지 않은 (SA에 올라가지 않은) 파일 
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

```

![Screen Shot 2021-06-21 at 오후 3.42](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%203.42.png)



add 명령어의 사용법

```bash
$ git add . # 현재 디렉토리(하위 디렉토리 포함)의 모든 요소를 Staging Area로 올린다.
$ git add a.txt # 특정한 파일만 SA로 올린다.
$ git add folder # 특정한 폴더(폴더 내부 파일 포함)만 올린다.
```



왜 add(SA)가 필요할까?

- 버전을 한번에 기록하는 것이 아니라 따로 기록할 수 있음!





## commit

- 커밋을 통해서 하나의 '버전'으로 기록됨!
- 커밋은 고유한 해시값으로 기록 

```bash
$ git commit -m "a.txt 파일 수정 완료" # -m 뒤에 나오는 문구는 해당 버전이 어떤 변경 사항을 갖고 있는지 간단하게 설명하는 메시지(커밋 메시지)
[master (root-commit) 33183b2] a.txt 파일 수정 완료
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```



커밋 목록은 `log` 명령어를 통해서 확인 가능

```bash
$ git log
commit 33183b2f3040fd8ddae64ac79206e43d8b0bad60 (HEAD -> master) 
Author: justin kim <edujustin.hphk@gmail.com> # 초기에 설정한 내용 -> commit(버전)을 누가 했는지 기록하기 위함
Date:   Mon Jun 21 15:49:40 2021 +0900

    a.txt 파일 수정 완료 # commit 메시지
```

![Screen Shot 2021-06-21 at 오후 3.54](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%203.54.png)



```bash
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
$ git log --oneline # commit을 간단하게 보는 방법
33183b2 (HEAD -> master) a.txt 파일 수정 완료

```





## status

- working directory와 staing area 공간의 파일 상태를 확인할 때 사용하는 명령어

![Screen Shot 2021-06-21 at 오후 4.08](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.08.png)



## 추가 commit 쌓기

```bash
$ git status
On branch master
Changes not staged for commit: # commit을 위한 변화 사항이 아직 staged(무대 위로 올라가지 않은 상황) 되지 않은 요소
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

Untracked files: # 여전히 untracked인 상태(한번도 commit하지 않음)
  (use "git add <file>..." to include in what will be committed)
        b.txt

no changes added to commit (use "git add" and/or "git commit -a")
```



![Screen Shot 2021-06-21 at 오후 4.15](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.15.png)

```bash
```

```bash
$ git add a.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   a.txt # commit 되어질 변화 사항들

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt


```

```bash
$ git commit -m "Edit a.txt"
[master 307badc] Edit a.txt
 1 file changed, 1 insertion(+)

$ git log --oneline
307badc (HEAD -> master) Edit a.txt
33183b2 a.txt 파일 수정 완료
```





```bash
$ git add .

$ git commit -m "Finish b.txt"
[master bf2ffc8] Finish b.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 b.txt

$ git log --oneline
bf2ffc8 (HEAD -> master) Finish b.txt
307badc Edit a.txt
33183b2 a.txt 파일 수정 완료
```



최종 정리

![Screen Shot 2021-06-21 at 오후 4.25](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.25.png)



## 주의 해야 할 사항!!

- `$ git init` 명령어는 git이 관리하려고 하는 폴더의 '최상단 폴더'에 딱 한번 작성해야 합니다.
- `git init` 을 수행한 폴더 내부에 다른 폴더를 만들고 다시 `git init` 하면 안됨!!!!!

