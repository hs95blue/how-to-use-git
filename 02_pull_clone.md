## pull

- 원격 저장소의 변경 사항을 받아온다. (업데이트)
- commits(커밋 내역)를 기반으로 변경 사항을 가져온다고 생각하자!

```bash
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 804 bytes | 100.00 KiB/s, done.
From https://github.com/edujustin-hphk/practice
 * branch            master     -> FETCH_HEAD
   e793bd3..4301f0a  master     -> origin/master
Updating e793bd3..4301f0a
Fast-forward
 a.txt | 1 +
 1 file changed, 1 insertion(+)
```



- 단, github에서 commit을 직접 발생 시키는 행위는 지양해야 함 





## clone

- 원격 저장소 전체를 복제
- clone 받은 프로젝트는 이미 `$ git init`을 한 것과 동일하게 git 저장소로 초기화 되어있음!
- `remote`도 추가 되어있음!!!

```bash
$ git clone clone할 저장소 URL

# clone 
$ git clone https://github.com/edujustin-hphk/TIL.git

# 저장소도 이미 지정되어 있음
$ git remote -v
origin  https://github.com/edujustin-hphk/TIL.git (fetch)
origin  https://github.com/edujustin-hphk/TIL.git (push)

# 만약 원격 저장소의 이름을 사용하지 않고 다른 이름을 쓰려고 하면? 공백을 두고 입력한다.
$ git clone https://github.com/edujustin-hphk/TIL.git TIL-test
Cloning into 'TIL-test'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```



## push & pull(+clone) 시나리오

![Screen Shot 2021-06-22 at 오전 9.48](md-images/Screen%20Shot%202021-06-22%20at%20%EC%98%A4%EC%A0%84%209.48.png)

