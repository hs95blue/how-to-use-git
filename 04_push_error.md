# push error

- github에서 commit을 하나 남긴 상태 & local 컴퓨터에서 추가적인 commit을 남긴 상태 

- commit 이력이 다르기 때문에...! -> Merge를 통해 이력을 하나로 만들어 줘야 한다!!

```bash
$ git push origin master
To https://github.com/edujustin-hphk/practice.git
 ! [rejected]        master -> master (fetch first)

# push하는 것에 실패함...
error: failed to push some refs to 'https://github.com/edujustin-hphk/practice.git'

# update가 거절됨...원격 저장소에 있는 내역이 (너의) 로컬에 없어..
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing

# 너는.. 원격 저장소의 내역을 통합 하기를 원할거야...
hint: to the same ref. You may want to first integrate the remote changes
# git pull 해보면 좋지 않을까...? 다시 push하기 전에...?
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```



pull 진행

- vs code 에디터가 나타냄
- x 눌러서 종료하면 끝

```bash
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 673 bytes | 61.00 KiB/s, done.
From https://github.com/edujustin-hphk/practice
 * branch            master     -> FETCH_HEAD
   4301f0a..cd1741e  master     -> origin/master
Merge made by the 'recursive' strategy.
 b.txt | 1 +
 1 file changed, 1 insertion(+)

```



커밋 이력 확인

```bash
$ git log --oneline
6392bec (HEAD -> master) Merge branch 'master' of https://github.com/edujustin-hphk/practice  # local 저장소의 최신 commit
9a1c98a a.txt를 local에서 수정했습니다!
cd1741e (origin/master) b.txt 수정 in github # 원격 저장소의 최신 commit
4301f0a github에서 남긴 commit 메시지
e793bd3 Edit README
ff245df Finish b.txt
aa4626b Finish a.txt
72c550d Finish README file
```



최종적으로 local commit 원격 저장소에 반영하기 위해 push 진행

```bash
$ git log --oneline
6392bec (HEAD -> master, origin/master) Merge branch 'master' of https://github.com/edujustin-hphk/practice
9a1c98a a.txt를 local에서 수정했습니다!
cd1741e b.txt 수정 in github
4301f0a github에서 남긴 commit 메시지
e793bd3 Edit README
ff245df Finish b.txt
aa4626b Finish a.txt
72c550d Finish README file
```



`HEAD`는 현재 위치한 브랜치의 최신 commit을 가리킴!

```bash
$ cat .git/HEAD
ref: refs/heads/master
```