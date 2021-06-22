# gitignore

> git으로 관리하고 싶지 않은 파일/폴더 리스트를 작성할 수 있음. 특정 파일을 git으로 관리하지 않음

- 개인정보, 개발 환경과 관련된(==외부에 노출이 되면 안되는 정보) 
  - token, AWS key 외부에 노출이 되면 안됨 (-> github에 올라가면 안됨)



**기본 세팅**

```bash
$ git init

$ touch a.txt b.txt token.txt
$ mkdir venv
$ touch venv/my_text.txt
```



아래와 같은 형태로 git이 관리하지 않게 만들 수 있다.

```bash
venv/ # 특정한 폴더 
token.txt # 특정한 파일
*.txt # 특정한 확장자를 가진 파일
```



일반적으로  `git init`을 수행한 곳(== 최상단 디렉토리)에 작성한다.



## gitignore.io

https://www.toptal.com/developers/gitignore

- 운영체제, 언어, 프레임워크 등의 환경에서 (일반적으로) git으로 관리하지 않는 요소를 미리 만들어 놓은 사이트
- 검색 후 '생성' 버튼을 누르고 해당 내용을 전체 선택(`ctrl` + `a`)하고 `.gitignore` 파일에 붙여넣으면 끝!