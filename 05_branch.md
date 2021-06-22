# Branch (command)

기본 준비

```bash
$ mkdir branch_practice && cd branch_practice
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/branch_practice/.git/
$ git add .
$ git commit -m "Finish a.txt"
[master (root-commit) c468bb7] Finish a.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```



- 브랜치 생성

  ```bash
  $ git branch 브랜치이름
  
  $ git branch feature
  ```

- 브랜치 목록 확인

  ```bash
  $ git branch
    feature
  * master
  ```

- 브랜치 이동

   ```bash
   $ git checkout 브랜치이름
   
   $ git checkout feature
   
   ```

- 브랜치 생성 & 이동

  ```bash
  $ git checkout -b feature2
  Switched to a new branch 'feature2'
  
  # 브랜치 목록 확인
  $ git branch
    feature
  * feature2
    master
  ```

- 브랜치 병합

  ```bash
  $ touch b.txt
  $ git add .
  $ git commit -m "Finish b.txt"
  [feature2 eace0c9] Finish b.txt
   1 file changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 b.txt
   
   $ git log --oneline
  eace0c9 (HEAD -> feature2) Finish b.txt
  c468bb7 (master, feature) Finish a.txt
  
  # master 브랜치 이동
  $ git checkout master
  Switched to branch 'master'
  
  # merge
  $ git merge feature2
  Updating c468bb7..eace0c9
  Fast-forward
   b.txt | 0
   1 file changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 b.txt
   
   $ git log --oneline
  eace0c9 (HEAD -> master, feature2) Finish b.txt
  c468bb7 (feature) Finish a.txt
  
  ```

- 브랜치 삭제

  ```bash
  $ git branch -d feature2
  Deleted branch feature2 (was eace0c9).
  
  $ git branch
    feature
  * master
  ```

- 브랜치 강제 삭제

  - 완전히 merge되지 않은 브랜치를 삭제 하려고 할 때 에러 발생

  ```bash
  $ git branch -D feature
  Deleted branch feature (was 1277106).
  
  ```

  