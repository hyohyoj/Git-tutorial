# Git-tutorial

### 사전준비
내 계정 깃허브에서 새로운 저장소 생성, 주소 복사
깃에 업로드 할 프로그램 폴더로 이동

## 깃허브에 파일 등록하기
> git 시작
```
git init
```

> origin(일반적으로 원격저장소 별칭으로 사용)에 깃허브 추가(연결)
```
git remote add origin {github repository URL}
```

> stage 에 파일 등록(스테이징한다 라고도 말함)
```
git add {file name}
```

> 폴더에 있는 모든 파일 추가
```
git add .
```

> staged 파일들을 확인할 수 있다
```
git status
```

> add 한 파일 취소
```
git -- reset
```

> commit 등록 (stage에 있는 파일이 local repository에 저장됨)
```
git commit -m {"commit message"}
```

> 커밋한 파일이 github(remote repository)에 등록
```
git push {}

git push origin main
```

ㄴ> ~~깃허브에서 직접 readme 파일을 수정 후 pull을 안 해줘서 rejected 에러 -> git push -u origin +master -> 작성한 readme 파일이 날라가버림.. 근데 push는 성공~~

## 깃허브 repository를 README 파일과 함께 생성했을 때 push rejected error
+ 원인
  + 원격 저장소에서 이루어진 readme.md를 추가하는 커밋이 로컬 저장소의 커밋 로그에는 없기 때문.


- 또 다시 에러 
```
git pull origin main
```
**-- fatal: refusing to merge unrelated histories**

공통되는 commit이 없기 때문에 pull 명령어 사용 불가. 

- 해결!
```
git pull origin <branchname> --allow-unrelated-histories
```
연관 히스토리가 없어도 pull 할 수 있게 --allow-unrelated-histories 명령어 사용


## 깃허브에서 파일 가져오기
> github에서 local repository로 가져옴
```
git fetch
```

> local 레파지토리랑 깃의 레파지토리를 완전히 동일시
```
git merge
```

> git fetch, git merge를 동시에 사용
```
git pull
```


## 깃 브랜치명을 main으로 바꾸기
defaultBranch를 main으로 설정 후

> main 브랜치로 브랜치명 변경
```
git branch -m master main
```

> commit 가져오기
```
git fetch origin
```

> origin/main 으로 연결된 정보 변경
```
git branch -u origin/main main
```

> origin/main 으로 HEAD 연결정보 수정
```
git remote set-head origin -a
```

## 리모트 저장소에서 지워진 브랜치를 로컬에 반영
> local에서 안 쓰는 브랜치 삭제
```
git pull --prune
```

## 브랜치
> 브랜치 목록 확인
```
git branch
```

> 브랜치 생성
```
git branch <branchname>
```

> 브랜치 변경
```
git checkout <branch>
```

> 브랜치 작성 & 체크아웃
```
git checkout -b <branch>
```

> 브랜치 삭제
```
git branch -d <branchname>
```

## 커밋 메시지 수정
> 가장 최근 commit 메시지 수정
```
git commit --amend -m "수정할 커밋 메시지"
```
또는
```
git commit --amend
```
vi 터미널에서 메시지 수정 후 wq로 저장
> 리모트에 이미 push 했을 경우
위의 방법으로 local에서 commit 메시지를 변경한 후
```
git push --force 브랜치 이름
```
강제로 원격에 다시 덮어쓰는 방법 (권장되는 방법은 아님 협업 중엔X)
