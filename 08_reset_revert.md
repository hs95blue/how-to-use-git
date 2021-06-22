# reset vs revert

## 1. reset

>  **시계를 과거로 돌려버림!!!**

- 특정 커밋으로 되돌아가며 특정 커밋 이후의 모든 이력은 사라진다. 
- 파일의 상태는 옵션으로 결정한다.



**3가지 옵션**

1. `--soft`

   - reset하기 전까지 했던 SA, WD 작업은 그대로 남겨둠
   - **돌아가려는 커밋으로 이동!!**
   - 이후의 commit된 파일들을 SA로 돌려놓는다. (==commit 이전의 상태)
   - 바로 다시 commit을 할 수 있는 상태가 된다!

2. `--mixed`

   - SA reset, WD 작업물만 남겨둠
   - **돌아가려는 커밋으로 이동!!**
   - 이후의 commit된 파일을 WD로 돌려놓는다. (==add를 하기 전 상태)

   - 기본값

3. `--hard`

   - **돌아가려는 커밋으로 이동!!**
   - 이후의 commit된 파일을 모두 WD에서 삭제
   - 단, Untracked된 파일은 Untracked 

   - reset을 하기전 SA, WD 모든 작업물을 reset



undoing 작업한 결과물로 진행



```bash
$ git log --oneline
10a4169 (HEAD -> master) foo & bar # 현재 우리는 여기에 있음
e006b80 Finish all things
5ab6f04 first commit

# 특정한 hash 값(시점 --> commit)의 시점으로 이동
$ git reset --hard
HEAD is now at 10a4169 foo & bar

# commit 시점 
$ git log --oneline
5ab6f04 (HEAD -> master) first commit

```

- reset을 통해서 과거로 돌아가게 되면 돌아간 이후의 commit은 모두 사라짐 

- commit의 history가 바뀌기 때문에 **다른 사람과 공유하는 브랜치가 있는 경우 절대 사용하면 안됨**





## 2. revert

> **특정한 사건을 없었던 일로 만들어버림!!**

- 이전 커밋 이력은 그대로 남겨둠
- 커밋 히스토리의 변경 없이 해당 커밋의 내용만을 삭제한 상태의 새로운 커밋을 남김



```bash
$ touch c.txt d.txt

$ git add c.txt
$ git commit -m "Add c.txt"
[master a4fcf1a] Add c.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 c.txt


$ git add d.txt
$ git commit -m "Add d.txt"
[master aaff59d] Add d.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 d.txt
 
 # 현재 상태 -> commmit 3개
 $ git log --oneline
aaff59d (HEAD -> master) Add d.txt
a4fcf1a Add c.txt
5ab6f04 first commit

```

vs code 에디터 창 -> 종료 

```bash
Revert "first commit"

This reverts commit 5ab6f040e09cef5d36efca1b8127e2d562d80aef.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
# Changes to be committed:
#	deleted:    README.md
#	deleted:    a.txt
#
```



```bash
$ git log --oneline
7da838f (HEAD -> master) Revert "first commit" # 5ab6f04 시점으로 돌아감!(실제 파일이 삭제됨)
aaff59d Add d.txt
a4fcf1a Add c.txt
5ab6f04 first commit

```

- `5ab6f04`라는 시점으로 돌아감 
  - 그럼 reset과의 차이점은??? 
  - reset은 commit 이력이 없기 때문에 다시 돌아갈 수 없지만
  - revert는 이전 commit 이력이 모두 남겨져 있기 때문에 다시 돌아갈 수 있다!



- 다른 사람과 공유하는 브랜치에서 이전 커밋을 수정하고 싶을 때 사용합니다.
- 커밋 이력이 변경되지 않기 때문에 충돌이 발생하지 않습니다.



## 정리

![Screen Shot 2021-06-22 at 오후 3.23](md-images/Screen%20Shot%202021-06-22%20at%20%EC%98%A4%ED%9B%84%203.23.png)