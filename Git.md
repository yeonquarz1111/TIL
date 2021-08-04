## Git

- 분산버전관리시스템으로 코드의 버전을 관리하는 도구
- 2005년 리누스 토르발스가 개발
- 컴퓨터 파일의 변경사항 추적, 여러 명 사용자들 간에 해당 파일들의 작업을 조율

### 분산버전관리시스템 (DVCS)

- 중앙집중식버전관리시스템은 중앙에서 버전을 관리하고 파일을 받아서 사용
- 분산버전관리시스템은 원격 저장소를 통해 협업, 모든 히스토리를 클라이언트 공유

### 기본 흐름

1. 작업하면
2. **add** 하여 staging area에 모아
3. **commit**으로 버전 기록 



### CLI 환경

![image-20210804113315259](C:\Users\연수\AppData\Roaming\Typora\typora-user-images\image-20210804113315259.png)

- CLI (Command Line Interface) : 명령을 줄 단위로 하는 것

![image-20210804113454486](C:\Users\연수\AppData\Roaming\Typora\typora-user-images\image-20210804113454486.png)

- GUI (Graphic User Interface) 

### CLI 명령어

- ls : 목록. 파일 열기

  ```bash
  $ ls
  1.txt
  ```

- touch : 파일 만들기

  ```bash
  $ touch <파일명>
  $ touch README.md
  ```

- pwd (Print wording directory) : 현재 작업 디렉토리 출력

  ```bash
  $ pwd
  /c/Users/lec/Desktop/실습1
  ```

- mkdir (make directory) : 디렉토리 만들기

  ```bash
  $ mkdir test
  ```

- cd test (change directory test) : 디렉토리 이동

  ```bash
  $ cd test
  ~/Desktop/실습1/test $ cd ..
  ~/Desktop/실습1 $
  ```

  - `..` : 상위 디렉토리
  - `.` : 현재 디렉토리

---

### Git 명령어

#### 저장소 만들기

```bash
 $ git clone 주소
```

```bash
 $ git init
```

- git 저장소를 만들어 git으로 관리
- .git 폴더가 생성
- git bash 에서는 (master) 라는 표기를 확인 가능

#### 작업하기

```bash
$ git add <file>
```

- working directory 상의 변경 내용을 staging area에 추가하기 위해 사용
- 작업 내용을 add 하면 다음 commit 에 적용된다
- untracked 상태의 파일을 staged 로 변경
  - staging area : 임시 저장 공간

```bash
$ git add .
```

- 디렉토리 안의 모든 파일을 add 한다



![](C:\Users\연수\Desktop\제목 없음.png)

```bash
$ git commit -m '커밋메시지'
```

- staged 상태의 파일을 commit함
- commit 으로 버전별 스냅샷처럼 기록 가능



#### 상태 보기

```bash
$ git status
```

- commit 할 파일이 있는지 확인

```bash
$ git log
commit 0ccc720b179d56908bd24b839bf3de1f743d095d (HEAD -> master)
Author: yeonquarz1111 <syouo@naver.com>
Date:   Wed Aug 4 14:26:38 2021 +0900

   	<a 추가>
```

- git 의 log 내역을 볼 수 있음

#### 원격저장소

```bash
$ git remote add origin url
```

- 깃아, 원격저장소(remote) 추가해줘. (add) origin 이라는 이름으로 url을
- origin 이름 바꿔도 되나, 일반적으로 원격저장소는 origin으로 부름

```bash
$ git push origin master
```

- 깃아 원격저장소 origin에 master를 push 해줘



### 커밋 실습

```bash
# 바탕화면에 test 폴더 만들고,
# test 폴더 우클릭 - git bash here
# test 폴더에 a.txt 파일 저장

yeonsoo@DESKTOP-SVP99GP MINGW64 ~/Desktop/test
$ pwd
/c/Users/연수/Desktop/test # 현재 위치 확인

$ git init
Initialized empty Git repository in C:/Users/연수/Desktop/test/.git/ # 깃 폴더 생성

$ git add a.txt # a.txt 파일 add 하기

$ git commit -m '<a 추가>'
[master (root-commit) 0ccc720] <a 추가> # a 추가라는 메시지와 함께 커밋
 1 file changed, 1 insertion(+)
 create mode 100644 a.txt
```



#### 명령어 번역

```bash
$ git status
on branch master
# 트래킹되고 있지 않은 파일들
Untracked files:
# staging area에 포함시키기 위해서는 git add를 해
(use "git add <file> ..." to include in what will be committed)
	new.txt
#커밋하기 위해 추가된 것은 없는데 untracked files는 존재한다
# working directory -> 파일 있어
# staging area -> 파일 없어
nothing added to commit but untracked files present (use "git add" to track)
```

```bash
$ git status
on branch master
# 커밋될 변경사항들 (staging area)
changes to be committed:
	(use "git restore --staged <file>... " to unstage)
		new file:	new.txt

# staged x (커밋을 위해)
# working directory
Changes not staged for commit:
	(use "git add <file>..." to update what will be committed")
	(use "git restore <file>..." to discard changes in working directory)
		modified:	2.txt
	
# 트래킹 x
# working directory
Untracked files:
	(use "git add <file>..." to include in what will be committed)
	hi.txt
```



#### Bash에 Github ID, 이메일 입력하기

```BASH
$ git config --global user.name 깃허브 아이디
```

```BASH
$ git config -- global user.email 깃허브 이메일 주소
```

```bash
$ git config --global -l
user.name=yeonquarz1111
user.email=syouo@naver.com
```

- 제대로 입력되었는지 확인 



#### 커밋 완료 후 Git 에 push 하기

1. `계정 아이콘 - settings - Repositories` 에서 이름 master로 업데이트 하기

   (최근 main 으로 바뀌는 추세이지만 예전부터 master를 써서 이해를 쉽게 하기 위함)

2. 새로운 레포지토리 만들기

3. 해당 내용 git bash에 복붙 

![image-20210804151518349](C:\Users\연수\AppData\Roaming\Typora\typora-user-images\image-20210804151518349.png)

3.  git bash에 push 명령어 입력

```bash
$ git push origin master # push 명령어
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 217 bytes | 217.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/yeonquarz1111/test.git
 * [new branch]      master -> master
```

---



### 파일 라이프사이클

- Tracked : 이전부터 버전으로 관리되고 있는 파일
  - unmodified : git status에 나타나지 않음
  - modified : `Changes not staged for commit`
  - staged : `Changes to be committed`
- Untracked : 버전으로 관리된 적 없는 파일 (파일을 새로 만든 경우)



---



### 클론 vs 압축 다운로드

- 클론으로 받기
  - .git 폴더가 있으며 모든 버전을 받은 것

- 압축으로 받기

  -  현재 버전만 가져온 것

    