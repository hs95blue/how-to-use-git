# undoing

기본 준비

```bash
$ mkdir undoing && cd undoing
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/undoing/.git/
$ touch a.txt README.md


```

## 1. 파일 상태를 Unstage로 변경하기

> **Staging Area(INDEX)와 Working Directory를 넘나드는 방법**

- 따로 따로 커밋을 하려고 했지만 실수로  `git add .`라고 해버린 상황



```bash
$ git add .
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage) # 무대 밖으로 내리기 위해서는 이 명령어를 쓰세요!
        new file:   README.md
        new file:   a.txt

```

```bash
$ git rm --cached a.txt
rm 'a.txt'

$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md # 무대 위에 올라간 친구들 -> SA

Untracked files: # 무대 위에 올리지지 않은 친구들 -> WD 
  (use "git add <file>..." to include in what will be committed)
        a.txt

```

![Screen Shot 2021-06-22 at 오후 2.13](md-images/Screen%20Shot%202021-06-22%20at%20%EC%98%A4%ED%9B%84%202.13.png)



```bash
$ git add .
$ git commit -m "first commit"
[master (root-commit) 5ab6f04] first commit
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
 create mode 100644 a.txt
```





## 2. `restore`

- **두 개의 파일을 모두 수정**하고나서 따로 따로 커밋을 하려고 했지만 실수로  `git add .`을 해버린 상황



```bash
# 현재 working directory에 있는 상황 
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")

```



```bash
# Staging Area에 올라간 상황
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
        modified:   a.txt
```



```bash
$ git restore --staged a.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt
```





## 첫 번째와 두 번째 차이?

- 둘 다 SA에서 WD로 내려간 것은 맞다!



```bash
$ touch b.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md # 이미 commit을 하고 난 이후에 수정 -> add한 상황(SA)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt # 이미 commit을 하고 난 이후에 수정 x -> add 전(WD)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt # commit 이력 없이 WD에 있음 


```

1. `$ git rm --cached <file>`
   - commit 이력이 없을 때 SA -> WD
2. `$ git restore --staged <file>`
   - commit 이력이 있을 때 SA -> WD





## 2. Modified된 파일 되돌리는 방법?

- **(add되어 있지 않은 -> Woking Directory에 있는)수정된(modified) 파일을 되돌리는 방법**

- 기존 파일을 덮어쓰는 방식으로 진해하기 때문에 원래 내용은 모두 사라진다!
- **수정한 내용이 정말로 마음에 들지 않을 경우만 사용해야 한다. 해당 명령어를 수행하면 '절대로' 다시 원래로 돌릴 수 없다!!!!**



```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

$ git restore a.txt

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

```



## 3. 완료한 커밋 수정

```bash
$ git commit --amend
```

1. commit 메시지를 잘못 작성했을 때 -> 바로 직전!!
2. 특정한 파일을 빼놓고 commit을 했을 때 



- 공개된 저장소(github, gitlab, bitbucket)에 push한 commit 메시지는 절대로 수정 금지!!!
- commit hash 값이 변경되기 때문에!!



### 3-1. 커밋 메시지 수정

- 마지막으로 작성한 커밋 메시지를 되돌리는 방법
- 주의해야 할 것은 직전 commit 메시지만 수정 가능하다.

```bash
$ git add .
$ git commit -m "inish all things"
[master 4f4bcb5] inish all things
 2 files changed, 1 insertion(+)
 create mode 100644 b.txt

```

```bash
# vs code가 열리고 commit 메시지 수정 후 닫기
$ git commit --amend
hint: Waiting for your editor to close the fi[master e006b80] Finish all things
 Date: Tue Jun 22 14:37:02 2021 +0900
 2 files changed, 1 insertion(+)
 create mode 100644 b.txt
 
 $ git log --oneline
e006b80 (HEAD -> master) Finish all things
5ab6f04 first commit


```



### 3-2. 어떤 파일을 빼놓고 commit을 한 경우

- foo와 bar 파일 모두를 하나의 commit(변경 사항)으로 만들고 싶었는데 foo 파일만 commit한 경우

```bash
$ touch foo.txt bar.txt
$ git add foo.txt
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   foo.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        bar.txt
        
$ git commit -m "foo & bar"
[master 3805329] foo & bar
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 foo.txt

# bar.txt가 commit에 포함되지 않은 상태!
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        bar.txt

nothing added to commit but untracked files present (use "git add" to track)


```

```bash
# SA bar.txt를 올린다.
$ git add bar.txt

# (원래라면)
$ git commit -m "Add bar.txt" # 하지만 이렇게 하면 추가적인 commit이 생겨버림!

foo & bar

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Tue Jun 22 14:41:19 2021 +0900
#
# On branch master
# Changes to be committed:
#	new file:   bar.txt
#	new file:   foo.txt
#




```

```bash
$ git status
On branch master
nothing to commit, working tree clean

# 하나의 commit에 foo.txt와 bar.txt의 변경 사항이 모두 포함됨!!!
$ git log --oneline
10a4169 (HEAD -> master) foo & bar
e006b80 Finish all things
5ab6f04 first commit

```

