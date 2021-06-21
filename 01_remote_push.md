[toc]

- toc -> table of content

- 목차 만들기

  - `[toc]` + enter

  



# 원격 저장소(remote repository)

1. 초기화 된 git 저장소 준비

2. Github repo 생성

   ![Screen Shot 2021-06-21 at 오후 4.58](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.58.png)

   ![Screen Shot 2021-06-21 at 오후 4.46](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.46.png)

3. Repository default branch 

   - main -> master로 변경

   ![Screen Shot 2021-06-21 at 오후 5.01](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%205.01.png)





## 명령어

### 원격 저장소 주소 추가

- "git아! 원격 저장소(remote)를 추가(add)해줘 origin이라는 이름으로!!!"

- origin은 저장소 URL에 별명(?)을 붙였다고 생각하면 이해하기 편함!!

```bash
$ git remote add origin https://github.com/edujustin-hphk/practice.git # 저장소 URL은 본인 repo의 URL을 등록하면 됨
```

![Screen Shot 2021-06-21 at 오후 4.51](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.51.png)

### 원격 저장소 목록 보기

```bash
$ git remote -v
origin  https://github.com/edujustin-hphk/practice.git (fetch)
origin  https://github.com/edujustin-hphk/practice.git (push)
```



만약 등록한 remote url을 삭제하고 싶다면?

```bash
$ git remote rm origin # rm -> remove
```



## 원격 저장소에 업로드(push)

최초 1회는 로그인 필요

- "git아 push해줘! origin이라는 이름의 원격 저장소로 master 브랜치를!!!"

![Screen Shot 2021-06-21 at 오후 4.55](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.55.png)





- 원격 저장소에는 commit 이력이 업로드 된다.
  - commit 이력이 없다면 push가 되지 않음!!
  - 두번째 push 부터는 `$ git push`라고만 입력해도 업로드 가능

```bash
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 277 bytes | 277.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/edujustin-hphk/practice.git
   72c550d..aa4626b  master -> master
```



## 정리

![Screen Shot 2021-06-21 at 오후 5.16](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%205.16.png)



## TIL (Today I Learned)

- 개발자들의 연습장?

- README -> 나를 읽어줘! 
  - 대소문자는 구분하지 않지만 파일명은 반드시 readme로 작성!