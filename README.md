## How to use Git

### 1. Install Git
[Git](https://desktop.github.com/)을 다운받고 설치하여 Git Shell을 실행한다.

### 2. Creating Your Online Repository in github.com 
github에서 git-test라는 새로운 repository를 만든다.

### 3. Creating Your Local Repository
	mkdir git-test
명령어로 github에 만든 repository와 같은 이름의 디렉토리를 만든다. 

	cd git-test
방금 만든 디렉토리로 이동한다. (cd:change directory)

	git init
깃 저장소를 초기화한다. 저장소나 디렉토리 안에서 이 명령을 실행하기 전까지는 그냥 일반 폴더이다. 초기화한 후부터 git 명령어들을 줄 수 있다.

	echo "# git-test" >> README.md
README.md 파일을 생성하고 거기에 # git-test 라는 내용을 집어 넣는다.

	git status
README.md 파일이 untracked files 리스트에 있는 것을 확인할 수 있다. 이것은 git이 지금은 그 파일을 무시하고 있다는 것을 의미한다. git이 이 파일을 인식하게 하기위해 다음을 type 한다.

	git add README.md
README.md 파일을 add 했다. 이제는 지금까지의 이 프로젝트의 snapshot을 찍을 시간 즉, "commit"할 시간이다. 

	git commit -m "first commit"
깃의 가장 중요한 명령어. 어떤 변경사항이라도 만든 후, 저장소의 “스냅샷”을 찍기 위해 이것을 입력한다. 보통 “git commit -m “Message hear.” 형식으로 사용한다. -m은 명령어의 그 다음 부분을 메시지로 읽어야 한다는 것을 말한다. 버전관리는 시간에 대해 유연성을 가지므로 현재형으로 작성해야 한다. 더 이전 버전으로 되돌아갈 수 있으므로 커밋을 했던 것을 적는 것이 아니라, 커밋한 것을 적어야 한다.

이제, 로컬에서 작업을 하고 github에 첫 커밋을 push 할 때이다. 하지만 아직 온라인 저장소를 로컬저장소와 연결하지 않았다.

### 4. Connect Your Local Repository To Your Github Repository
먼저, git에게 remote repository가 실제로 어디에 존재하고 있는지 알려줘야한다. git add 명령어를 사용 하기 전까지 git이 파일들을 인식하지 못했던 것 처럼 remote repository도 아직 인식하지 못한다. 

	git remote add origin https://github.com/[username]/git-test.git

(온라인에 있는 https://github.com/[username]/git-test.git repository를 origin으로 지정한다)
이제 git은 저기에 remote repository가 있고 거기에 local repository의 변경사항을 보내길 원한다는 것을 알게되었다. 확인하기 위해 다음을 type하여 확인한다.
	git remote -v
이 커맨드는 로컬 저장소가 알고있는 원격 remote origin의 목록을 보여준다. 

이제 github 원격 저장소로 변경사항을 업로드, 즉 push 해보자. 

	git push -u origin master
(u:upstream 첫번째올릴때만 쓴다, origin이라는 remote에, 저장소 master에 push 한다)

>from [GitHub For Beginners: Don’t Get Scared, Get Started](http://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/)

*=>summary*

	git init
	echo "# git-test" >> README.md
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/[username]/[projectname].git
	git push -u origin master

***

## 프로젝트와 git을 연결 한 후 파일을 수정하고 올릴땐

1. `git status` 로 바뀐파일 확인
   저장소 상태를 체크. 어떤 화일이 저장소 안에 있는지, 커밋이 필요한 변경사항이 있는지, 현재 저장소의 어떤 브랜치에서 작업하고 있는지 등을 볼 수 있다.
2. `git add 파일이름` or `git add --a` or `git add *` 로 올릴 내용을 add
3. `git commit -m "태그 내용"`
4. `git push origin master`
5. github id, password


***

## 다른사람이 push한 github에 있는 코드를 받아오려면

	git pull origin master

git pull: 로컬 컴퓨터에서 작업할 때, 작업하고 있는 저장소의 최신 버전을 원하면, 이 명령어로 깃허브로부터 변경사항을 다운로드한다(“pull”).

브랜치(**Branch**): 여러 명이 하나의 프로젝트에서 깃 없이 작업하는 것이 얼마나 혼란스러울 것인가? 일반적으로, 작업자들은 메인 프로젝트의 브랜치를 따와서(branch off), 자신이 변경하고 싶은 자신만의 버전을 만든다. 작업을 끝낸 후, 프로젝트의 메인 디렉토리인 “master”에 브랜치를 다시 “Merge”한다.

**git branch**: 여러 협업자와 작업하고 자신만의 변경을 원한다? 이 명령어는 새로운 브랜치를 만들고, 자신만의 변경사항과 화일 추가 등의 커밋 타임라인을 만든다. 당신의 제목이 명령어 다음에 온다. 새 브랜치를 “cats”로 부르고 싶으면, git branch cats를 타이핑한다.

**git checkout**: 글자 그대로, 현재 위치하고 있지 않은 저장소를 “체크아웃”할 수 있다. 이것은 체크하길 원하는 저장소로 옮겨가게 해주는 탐색 명령이다. master 브랜치를 들여다 보고 싶으면, git checkout master를 사용할 수 있고, git checkout cats로 또 다른 브랜치를 들여다 볼 수 있다.

**git merge**: 브랜치에서 작업을 끝내고, 모든 협업자가 볼 수 있는 master 브랜치로 병합할 수 있다. git merge cats는 “cats” 브랜치에서 만든 모든 변경사항을 master로 추가한다.

---
## github를 웹호스팅으로 이용하기
https://uiyoung.github.io/git-test/index.html  
https://opentutorials.org/course/2473/16117
