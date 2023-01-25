# git 기초편

기간: @2022년 11월 27일
작성일시: 2022년 11월 27일 오후 6:28
최종 편집일시: 2023년 1월 25일 오전 2:34
프로잭트 목적: git

# git 이란?

개발자와 기업들이 많이 사용

버전을 편리하게 관리하는데 도움을 줌

작업 파일을 원하는 순간으로 돌아갈 수 있음

협업 할 때 유용함

경쟁력 향상에 도움이 됨

# 준비물

-git 설치 - 필수

git이 이미 설치된지 확인 하려면 터미널에서 아래 명령어 입력해서 확인 가능

```bash
git --version
```

-터미널 (현업에서 많이 사용)

윈도우 터미널, iTerm2, cmder 등

-sourcetree (홈페이지에서 OS에 맞는 설치가능)

추가로 vscode를 설치해두면 좋다.

git에서 제공하는 모든 기능을 ui로 만든 어플리케이션은 찾기 힘들다

# Setup

## git의 모든 환경설정 [gitconfig]

깃에 관련된 모든 환경설정은 gitconfig라는 파일에 저장된다.

터미널에 아래 명령어로 모든 설정 들을 확인 가능

```bash
git config --list
```

터미널에서 파일로 확인 싶으면 아래 명령어 입력

```bash
git config --global -e
```

터미널 내에서 파일을 종료하고 싶다면 ‘:q’ 명령어로 나갈 수 있다. (or q or Nano editor 라면 ^X(=ctrl x)

## 터미널 말고 다른 editor로 파일을 열고싶다면? [code .]

text editor를 연결 해서 열어보고 파일을 열어보고 싶다면

사용하기 편한 text editor을 연결해서 사용 할 수 있다.(설정은 본인이 해야된다)

아래 명령어를 입력하면 본인이 연결되도록 설정한 text editor가 열린다.

(본인 같은 경우는 vscode를 이용했다.)

```bash
code .
```

이 ‘code .’를 editor와 연동해서 사용한다고 하면 아래 명령어를 사용한다.

```bash
	git config --global core.editor "code"  
//git config에 global적으로 설정하는 것 이라서 global을 작성하고 core.editor로 “code”작성
```

"code"만 사용한다면 다른 명령어를 수행 할 수 있도록 터미널이 계속 활성화 되어있다.

위 명령어를 입력하고 다시 한 번 환경설정을 파일로 확인 하는 명령어

```bash
**git config --global -e**
```

를 입력하면 연동되어 실행된 editor에서 ‘gitconfig’ 파일이 열린다.

```bash
git config --global core.editor "code --wait"
```

위와 같이 “code —wait”을 사용한다면 gitconfig 파일이 열린 상태에선 터미널이 다른 명령어를 수행 할 수 없는 대기 상태가 된다. 

파일을 종료하면 다시 터미널에서 명령어 입력이 가능하다.

## 사용자와 관련된 정보 설정

사용자 이름 설정

```c
git config --global user.name "하고 싶은 이름"
```

사용자 email설정

```c
git config --global user.email "하고 싶은 이메일"
```

설정된 이름과 이메일 확인

```c
git config user.name
```

```c
git config user.email
```

```c
git config --global core.autocrlf true
//윈도우 사용자라면 true
//맥,linux 사용자라면 input
```

운영체제 마다 에디터에서 새로운 줄 바꿈을 할 때 들어가는 문자열이 달라진다.

윈도우 같은 경우는 줄 바꿈 할 때 \r\n (\r : carriage-return , \n: line feed) 이 두개가 동시에 들어가고

맥에서는 \n만 들어간다.

이런 경우 git 리포지터리를 다양한 운영체제에서 쓰는경우 내가 수정하지 않았음에도 불고하고 줄 바꿈 문자열이 달라져서 git history나 git blame을 보는 데 문제가 있을 수 있다.

이 것을 방지해서 이를 수정하는 옵션이 autocrlf설정이다

윈도우에서 true로 설정하면 git에 저장할 때는 \r을 삭제 하게 되고, 다시 git에서 윈도우로 가져올 때는 자동으로 \r을 붙여준다.

맥에서는 input으로 설정하게 되면 git에서 받아올 때는 별다른 수정이 일어나지 않고 git에 저장할 땐 \r를 자동으로 삭제해준다.

맥에서는 \r이 붙지 않음에도 불구하고 이렇게 처리 해주는 것은 맥에서 이메일을 받아온 텍스트를 복사해서 붙여넣을 때 실수로 \r이 들어갈 수 있기 때문이다.

# git 공부 포인트

## git의 형식

git은 [git 명령어 옵션]으로 이루어져 있다.

여기서 사용되는 명령어는 무엇인지 어떤 일을 하는 아이인지 어떨 때 쓰면 좋은 지를 위주로 알아야 된다.

같은 명령어를 사용해도 어떤 옵션을 붙이냐에 따라서 조금씩 다른 방식으로 진행할 수 있다.

때문에 자주 쓰이는 명령어와 자주 쓰이는 옵션들을 위주로 공부한다.

git 공식 site에서 documentation 안에 레퍼런스에는 git에서 이용가능한 명령어들을 확인 할 수가 있다.

각각의 명령어를 클릭해서 들어가면 사용가능한 옵션들을 확인 가능하다.

[Reference](https://git-scm.com/docs)

# git 초기화/삭제

git은 어떤 폴더 등 초기화 해서 사용 가능하다.

git이라는 directory를 만들고 그 안으로 들어가보면 그 안에 아무런 파일도 없는 것을 확일 할 수 있다. 

<aside>
📌 파일 목록을 조회하는 명력어 ls , ls -al

</aside>

여기에 아래 명령어를 입력하게 되면 git이 초기화 되었다고 나온다.

```bash
git init
//Initialized empty Git repository in /mnt/d/projects/git/.git/ 라고 나온다
```

이 다음 다시 파일 목록 조회를 해보면 git이라는 숨겨진 폴더를 확인 할 수 있다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled.png)

<aside>
💡 폴더나 파일명 앞에 ‘.’이 붙어있으면 숨겨진 파일이다.

</aside>

이 숨겨진 폴더에 들어가 보면 git 리포지터리에 있는 다양한 정보들이 들어가 있는 것을 확인 할 수 있다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%201.png)

이곳은 git의 내부 구현 사항이 될 수 있다. git에 관련된 모든 정보들이 .git폴더 안에 저정되는 것을 확인해볼 수가 있다.

git을 초기화 하게되면 기본적으로 마스터 브랜치가 생성된다 (git project)

<aside>
💡 **브랜치 branch 란?**

'나무가지'란 뜻으로, 만들어 놓은 버전(master)의 복사본(branch)을 만들어 다른 방향으로 작업을 이어나가는 것.

예를들면

도전적인, 실험적인 개발을 이어나갈 때, 혹은 다른 방향으로 개발을 할 때,

본 ver(master)은 유지하고 복사 본(branch)을 만들어 이어나갈 수 있다.

이렇게 이어나간 브랜치는 나중에 삭제는 물론, 마스터와 병합도 가능하다.

</aside>

기본적으로 commit에서 버전을 관리하는 브랜치는 master 브랜치이다.

여기서 .git 폴더를 제거하면 git project가 아니게 된다.

<aside>
📌 파일을 제거하는 명령어 : rm , directory를 제거하려면 rm -r,rm -rf

</aside>

## UI로 git을 초기화, 관리 하는 방법

이미 기존에 초기화된 project가 있다면 repository를 추가해서 할 수 있다

- WSL2는 경로에 \\wsl$ 입력해서 찾아간다

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%202.png)

새로운 것을 만들고 싶다면 생성할 수도 있다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%203.png)

반복적으로 쓰이는 명령어를 단축해서 쓰고 싶다면 아래 명령어를 사용하면 된다.

```bash
git config --global alias.st status
//global 안에 alias를 이용해서 status를 st로 단축해서 쓴다.
```

> git status : git의 상태를 볼 수 있는 명령어
> 

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%204.png)

위 문장 처럼 git에는 명령어와 그 명령어에서 쓸수 있는 다양한 속성 값들이 있다. 어떤 속성 값이 있는지 확인하려면 명령어 다음에 —h라고 입력하면 간단하게 정보들을 확인해 볼 수가 있다.

아래 예시

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%205.png)

# Basics

## Workflow

git에는 총 3가지의 작업 환경이 나눠져 있다.

working directory : 우리가 프로젝트의 파일들을 수정하고 작업하고 있는 곳

staging area : 작업하다가 버전 히스토리에 저장 할 준비가 되어 있는 파일들을 옮겨놓는 곳

.git directory : 버전의 히스토리를 가지고 있는 곳

아래 예시처럼 적용된다.

1. a,b,c 파일 작업중

|  | working directory | staging area | .git directory |
| --- | --- | --- | --- |
| 파일 | a,b,c |  |  |
1. b,c 파일의 완성도가 어느정도 가춰짐

|  | working directory | staging area | .git directory |
| --- | --- | --- | --- |
| 파일 | a | b,c |  |
1. commit 이라는 명령어를 이용해서 staging area에 있는 파일들을 git 버전 히스토리에 저장

|  | working directory | staging area | .git directory |
| --- | --- | --- | --- |
| 파일 | a |  | 버전 히스토리1[b,c] |
1. 파일 a 같은 방식으로 진행될 수 있다.
    
    working directory > staging area > .git directory[버전 히스토리2[a]
    

이렇게 .git directory에 저장된 버전들은 checkout이라는 명령어를 이용해서 언제든지 원하는 버전으로 돌아갈 수 있다.

위와 같이 저장됨 git히스토리는 내 PC에만 보관 되기 때문에 내 컴퓨터에 문제가 생기면 히스토리를 잃을 수있다. 때문에 PC말고 githube와 같은 서버에 push라는 명령어를 통해서 나의 서버에 업로드가 가능하다. 그리고 서버에서 다시 로컬로 다운로드 받고 싶다면 pull이라는 명령어를 이용 할 수 있다.

<aside>
📌 스냅샷 : 변경된 파일 전체를 저장하지 않고, 파일에서 변경된 부분을 찾아 수정된 내용만 저장합니다. 마치 변화된 부분만 찾아 사진을 찍는 것과 같다고 하여 스냅샷 방식이라고 합니다.

</aside>

각각의 버전들의 정보가 어떻게 들어있는지 살펴보자면, 각각의 commit에는 스냅샷된 정보들을 기반으로 고유한 hashcode가 부가된다. 이들을 이용해서 우리가 버전 정보를 참조할 수가 있다.

commit에는 id뿐만 아니라 어던 버전인지 버전의 관련된 메시지, 작성자, 날짜 시간 같은 정보들도 함께 포함되어 있다.

### working directory

working directory는 untracked, tracked 두 가지로 나누어 볼 수 있다. 

tracked - git이 이미 알고있는(tracking) 파일이라면 tracked

untracked - 새로 만들어진 파일이거나 기존 프로젝트에서 git을 초기화 하게 되면 git이 파일에 대한 정보가 없는데 아직 tracking이 되지 않은 파일들을 untracked으로 분류한다.

tracked 에서도 지금 수정유무에 따라 unmodified(수정안됨), modified(수정된) 두 가지로 나눠 볼 수있다. 여기서 이전 버전과 비교해서 수정된 modified 파일만 staging area로 옮겨 갈 수 있다.

# 실습 1 (git add)

git이라는 directory안에 a,b,c 세 가지 파일을 만든다.

```bash
echo hello world! > a.txt
//hello world 라는 문자열을 a.txt파일에 저장
```

위와 같은 방식으로 b,c 파일도 만들어준다.

[echo (명령어) - 위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/Echo_(%EB%AA%85%EB%A0%B9%EC%96%B4))

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%206.png)

명령어 git status를 이용하면 현제 파일의 상태를 확인 할 수 있다.

working directory에 변경사항이 있고 commit 되지 않은 변경 사항이 생긴걸 확인 가능하다

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%207.png)

master branch 위에서 작업을 하고 있다 

아직 commits은 없다

untracked files 파일이 있다. (커밋할 항목에 포함하려면 "git add <file>..."을 사용하십시오.)

아직 commit할 것은 없지만 추적되지 않은 파일이 있음(추적하려면 "git add" 사용)

| working directory |  | staging area | .git directory |
| --- | --- | --- | --- |
| untracked | tracked |  |  |
| a.txt b.txt c.txt |  |  |  |

여기서 git이 tracking 할 수 있도록 staging area에 옮기려면 git add 명령어를 사용하면 된다.

```bash
git add a.txt
//commit할 준비가 되어있는 a.txt 파일을 staging area에 추가한다.
```

![commit 할 준비가 된 변경 사항: 새로운 파일: a.txt //////untracked files: b ,c](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%208.png)

commit 할 준비가 된 변경 사항: 새로운 파일: a.txt //////untracked files: b ,c

새로운 파일: a.txt

untracked files: b ,c

여기서 git add b.txt c.txt 로 b,c 파일을 staging area에 옮길 수 있지만

존재하는 .txt 파일을 모두 옮기고 싶다면 [다른 확장자도 가능 ex) git add *.c]

```bash
git add *.txt
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%209.png)

a,b,c가 다 commit 할 준비가 되어있다.

여기서 파일 수정이 일어난다면 수정된 파일을 확인할 수 있다.

```bash
echo dong >> a.txt
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2010.png)

이미 tracking 하고 있는 파일 중에 a.txt 파일이 modified(수정된)상태인 걸 확인 가능

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2011.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2012.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2013.png)

“git rm —cached <file>” 명령을 입력하면 다시 working directory로 이동할 수 있다.

```bash
git rm --cached *
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2014.png)

여기서 다시 add로 추가해준 다음 하나의 파일을 삭제해 준다면 삭제된 파일이라고 나온다

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2015.png)

![a 파일이 삭제되었다고 나옴](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2016.png)

a 파일이 삭제되었다고 나옴

여기서 “git add .” 명령어를 사용하면 모든 파일들을 포함해서 staging area에 추가된다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2017.png)

## gitignore

부수적으로 생긴 파일 같이 tracking하고 싶지 않은 파일이 있을 땐 gitignore을 사용하면 된다.

만약 .log파일들을 제외하고 싶다면 “echo *.log > .gitignore” 명령어로 gitignore파일에 입력해주면 된다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2018.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2019.png)

![.gitignore 에서 log.log를 지운 status](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2020.png)

.gitignore 에서 log.log를 지운 status

![.gitignore 에 log.log를 추가한 status](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2021.png)

.gitignore 에 log.log를 추가한 status

gitignore에 (tracking 하고 싶지 않은 파일에)

모든 .log 파일을 포함하고 싶다면 “*.log”

build 라는 디렉토리에 있는 모든 파일을 포함하고 싶다면 “build/” 

build 디렉토리 안에있는 .log만 포함하고 싶다면 “build/*.log”

이런 식으로 작성할 수 있다.

```bash
# 이렇게 #를 사용해서 주석

# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log

```

[https://git-scm.com/docs/gitignore](https://git-scm.com/docs/gitignore)
 참조

# git status

명령어에 대한 옵션을 알고 싶다면 명령어 뒤에 —h(help)를 붙이면 옵션들을 보여준다.

ex) git status —h

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2022.png)

git status 를 집고 넘어가면 아무런 옵션을 입력하지 않았을 땐 기본적으로 long옵션으로 적용된다.

s는 간단하게 표시 / b는 branch정보 확인

<aside>
📌 터미널 창을 깨끗하게 지우는 단축키 window : ctrl + L (or cls) / linux : clear or ctrl + L

</aside>

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2023.png)

왼쪽의 알파벳과 알파벳의 색이 상태를 나타낸다.

초록색 : staging area 

A : added 추가 됐다

빨강색 : working directory에 있다.

?? : traking되지 않은

M : modified (수정된)

# git diff

수정된 파일에서 어떤 부분이 수정이 됐는지 확인 하는 명령어 : git diff

옵션을 입력하지 않으면 working directory에 있는 것만 적용

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2024.png)

| diff --git a/b.txt b/b.txt | 코드 |
| --- | --- |
| git커멘드를 이용해서 a(=이전버전)의 b.txt와 b(=현재버전)의 b.txt를 비교한다 | 해석 |
| index a042389..f5be8ac 100644 | 코드 |
| git 내부적으로 파일을 참고하는 것 | 해석 |
| --- a/b.txt | 코드 |
| —-a(=이전버전)의 b.txt와  | 해석 |
| +++ b/b.txt | 코드 |
| +++b(=현재버전)의 b.txt를 비교한다 | 해석 |
| @@ -1 +1,2 @@ | 코드 |
| 이전 버전의 상태(-)는 첫번째 줄(1)까지 이고 현재 버전의 변경점(+)은 첫번째 줄(1)에서(,) 두번째 줄(2)까지 확인해라 | 해석 |
| hello world! | 코드 |
| 기존의 첫번째 줄 [hello world!] | 해석 |
| +add | 코드 |
| 추가된(+)[add] | 해석 |

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2025.png)

b.txt 파일에는 위 내용이 들어가 있다. 여기서 첫 번째 줄의 [hello world!]는 staging area에 들어가 있고 add는 들어가지 않아서(working directory) git diff를 이용하면 add만 볼 수 있다.

staging area의 변경사항을 확인하려면 —staged (또는 —cached) 옵션을 주면 된다.

```bash
git diff --staged
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2026.png)

---

[--- /dev/null] : 이전에는(—-) 아무것도 없었는데(null)

[+++ b/b.txt] : b.txt 파일이 추가 되었고

[@@ -0,0 +1 @@] : 이전에는(-) 어떤 줄도 없었지만 (0,0) 새로운 버전에는(+) 첫번째 줄에(1)

[+hello world!] : “hello world!”가 추가가 되었다.(+)

아래 c.txt도 마찬가지

터미널에서 확인하기 싫다면 아래와 같이 설정하면 된다. 일단 gitconfig 를 열고

```bash
git config --global -e
```

아래 코드를 추가해 준다.

```
[diff]
	tool =vscode        //diff 툴을 vscode로 이용하고
[difftool "vscode"]
	cmd = code --wait --diff $LOCAL $REMOTE //vscode의 명령어는 code 다음 터머널을 기다리고,diff를 이용하고 LOACL과 REMOTE를 비교한다.
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2027.png)

이 다음 ‘git difftool’ 을 이용하면 vs코드로 연결된다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2028.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2029.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2030.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2031.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2032.png)

# git commit

staging area에 있는 파일들을 버전으로 만드려면 git commit 명령어를 이용한다.

staging area에 있는 파일들을 git repository로 옮겨준다.

```bash
git commit
```

아무 옵션 없이 사용한다면 기본적인 템플릿이 나온다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2033.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2034.png)

보통은 여기에 Title과 Description을 적은 다음 파일을 닫으면

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2035.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2036.png)

[master (root-commit) 2a32be6] Title : 마스터 branch의 헤쉬코드 앞부분이 나와있다.(master (root-commit) 2a32be6) 그리고 우리가 입력한 Title이 나와있다.
2 files changed, 2 insertions(+) : 2개의 파일이 만들어졌고
create mode 100644 b.txt : b.txt가 처음으로 만들어짐
create mode 100644 c.txt : c.txt가 처음으로 만들어짐

git log를 사용하면 commit과 전체적인 헤쉬코드, 누가 언제 타이틀과 상세설명이 나와있다.

보통은 이것보단 git commit -m “masege”을 이용해서 메시지와 함께 한번에 commit을 한다.

```bash
git commit -m “masege”
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2037.png)

working directory에 있는 것을 add로 staging area로 옮기지 않고 바로 commit 할 수 있다.

```bash
git commit -am "masege"
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2038.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2039.png)

commit tip

git directory의 commit들은 버전별로 나누어서 관리하는 history이다.

우리가 어플리케이션을 만들때 의미있는 이름으로 기능별로 commit하는것이 좋다.

원치 않은 commit을 취소하기 편하다.

commit을 할 땐 commit 메시지에 맞도록 그 부분만 수정해서 commit을 하는것이 좋다.

커밋 오류가 발생했을때 

에러코드 128 fatal: detected dubious ownership in repository

window PowerShell을 관리자 권한으로 실행시켜 아래 명령을 입렵해준다

git config --global --add safe.directory '%(prefix)///wsl.localhost/Ubuntu/home/donghwan/project/gittest’

# Reset , Revert

- **reset** : 원하는 시점으로 돌아간 뒤 이후 내역들을 지웁니다.
- **revert** : 되돌리기 원하는 시점의 커밋을 거꾸로 실행합니다.

```bash
git reset --hard [commit된 원하는 버전의 hesh]
##원하는 버전으로 이동후 이후 히스토리 삭제
##[hesh]를 입력하지 않으면 최신 버전의 히스토리(commit)로 돌아감
```

현업에선 revert를 주로 사용

```bash
git revert [commit된 원하는 버전의 hesh]
##원하는 버전으로 이동하고 이동하기 전 단계로 돌아갈 수 있는것을 commit함
```

```bash
git revert --no-commit [commit된 원하는 버전의 hesh]
##돌아갈 수 있는 것을 commit하지 않고 원하는 버전으로 돌아감
##취소하고 싶다면 git reset --hard
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2040.png)

sourcetree에선 위 사진처럼 원하는 commit을 우클릭 후에 reset은 [이 커밋까지 현재 브랜치를 초기화] 를 선택, revert는 [커밋 되돌리기]를 선택해준다.

# Branch (가지)

## branch의 필요성

-프로젝트를 두개 이상의 모습으로 관리해야 할 때(현재 적용된 모습, 테스트용 모습)

-여러 작업들이 각각 독립되어 진행될 때(독립된 기능)

## branch 생성

아래 명령어 입력

sourcetree에선 상단의 브런치 버튼을 누르고 진행

```bash
git branch [branch name]
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2041.png)

## branch 목록

아래 명령어 입력

sourcetree에선 좌측에 나와있다. 더블 클릭으로 이동이 가능하다.

```bash
git branch
```

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2042.png)

## 다른 branch 로 이동

```bash
git switch [이동할 branch name]
```

## 생성과 동시에 이동

```bash
git switch -c [branch name]
```

## branch 이름 변경

```bash
git branch -m [현제 branch name] [바꿀 branch name]
```

## branch 삭제

```bash
git branch -d [삭제할 branch name]
##다른 branch로 가져오지 않은 내용이 있는 branch를 지울 때는
##git branch -D [삭제할 branch name] <<로 강제 삭제한다.
```

branch를 만들고 각 branch에서 commit을 해주면 우측 사진과 같이 나뉘어 진다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2043.png)

여기서 [git log] 명령어를 입력하면 현제 속해있는 branch에서의 log만 보여준다. 

전체적인 log를 보고싶다면 아래 명령어를 입력하면 된다.

```bash
git log --all --decorate --oneline --graph
```

# branch 합치기

## merge

두 브랜치를 한 커밋에 이어붙입니다.

기준이 되는 branch(ex master)로 이동해서 아래 명령어 입력

두  브랜치를 한 번에 적용 시키는 커밋이 생김

branch내역을 남기려면 사용

```bash
git merge [합칠 branch 이름]
```

소스트리에선 master로 이동한 후 우측 브랜치 리스트에서 우클릭 후 ‘현재 브랜치로 [] 병합’을 선택한다.

reset으로 돌아갈 수 있다.

merge한 branch는 필요없다면 삭제를 해도 된다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2044.png)

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2045.png)

## rebase

브랜치를 다른 브랜치에 이어붙입니다.

히스토리를 깔끔하게 정리되게 하려면 rebase를 이용

협업에는 사용하지 잘 사용하지 않는다

붙일 내용이 포함된 branch로 이동한다.(사라질 branch)

그 다음 아래 명령어를 입력한다.

<aside>
📌 이 아래로 기준이 되는 branch는 master branch, 붙일 내용이 포함된 branch는 slave branch라고 칭하겠습니다.

</aside>

```bash
git rebase [기준이 되는 branch (ex : master)]
```

소스트리에선 rebase할 브랜치로 이동한 후 우측 브랜치 리스트에서 우클릭 후 ‘현재 변경사항을 []에 재배치’을 선택한다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2046.png)

명령어를 입력한 직후에 slave branch는 합쳐진 상태이지만 기준 branch(master)는 합쳐지기 전의 상태에 있다.

이때 master branch로 이동해서 두 branch를 다시 merge로 합쳐준다.

![Untitled](git%20%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9%E1%84%91%E1%85%A7%E1%86%AB%20857947d232c2483d80fa83c89bbb07b1/Untitled%2047.png)

## branch 간 충돌 그리고 해결

다른 브랜치에서 같은 파일에 같은 줄에 서로 다른 내용을 입력하면 병합 할 때 충돌이 발생한다.

이 때는 프로그래머가 해결해야된다.

### merge에서 충돌

충돌이 일어나면 해당부분을 수정하고 git add와 commit을 해준다. 이때 commit을 할 땐 메세지가 자동 완성 된다. (위 merge랑 같음)

당장 충돌 해결이 어려운경우 아래 명령어를 입력해서 merge를 중단시킨다.

```bash
git merge --abort
```

### rebase에서 충돌

여기서는 해당 부분을 수정하고 git add를 한 다음 commit이 아닌 아래 명령어를 입력한다.

```bash
git rebase --continue
```

당장 충돌 해결이 어려운경우 아래 명령어를 입력해서 rebase를 중단시킨다.

```bash
git rebase --abort
```

rebase에선 branch의 commit을 다 붙이는 것 이기때문에 한 줄에서만 여러번의 충돌이 있을 수 있다. 그때마다 충돌 해결을 해줘야 한다.

마찬가지로 충돌 해결을 하고 rebase를 마쳤다면 master branch로 이동해서 merge로 마무리 해준다.

 

# Github

[Github 기초편](https://www.notion.so/Github-571a9fe901604472b3943fef97dddb4a)