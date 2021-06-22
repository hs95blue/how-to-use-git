[toc]

- toc -> table of content

- 목차 만들기

  - `[toc]` + enter

  



# 원격 저장소(remote repository)

1. 초기화 된 git 저장소 준비

2. Github repo 생성

   ![Screen Shot 2021-06-21 at 오후 4.58](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.58.png)

   Public은 누구든 자신의 github 저장소에 방문하면 해당 repo 정보를 확인할 수 있고 Private은 repo의 권한이 있는 사람만 열람이 가능하다.

   ![Screen Shot 2021-06-21 at 오후 4.46](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%204.46.png)

3. Repository default branch 

   - main -> master로 변경
   - 한번만 설정하면 됨
   
   ![Screen Shot 2021-06-21 at 오후 5.01](md-images/Screen%20Shot%202021-06-21%20at%20%EC%98%A4%ED%9B%84%205.01.png)





## 명령어

### 원격 저장소 주소 추가

- "git아! 원격 저장소(remote)를 추가(add)해줘 origin이라는 이름으로!!!"
- origin은 저장소 URL에 별명(?)을 붙였다고 생각하면 된다.
  - 만약 `origin`이라는 별명을 붙여주지 않는다면?
  - push 할 때 `$ git push origin https://github.com/edujustin-hphk/practice.git` 항상 이렇게 긴 URL을 모두 직접 입력해야 한다.
- 참고적으로 `origin`이라는 이름을 반드시 사용해야하는 것은 아니지만 일반적으로 `origin`을 사용한다.

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

- 최초 1회는 로그인 필요 -> 이때 git bash를 vscode에서 열어서 로그인을 진행 해야 한다.

  - `ctrl + shift + p` -> `>default` 입력 -> `Terminal: Select Default Profile` 클릭 -> `git bash 선택`

  - 이후 터미널 종료 후 재실행



- "git아 push해줘! origin이라는 이름의 원격 저장소로 master 브랜치를!!!"
  - 첫 로그인 화면에서는 그냥 `enter`만 눌러주자!

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
  - 대소문자는 구분하지 않지만 파일명은 반드시 readme로 작성해야 한다.
- README 파일은 일반적으로 해당 원격 저장소가 어떤 내용인지를 설명한다.

