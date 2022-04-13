# git-command
간단하게 자주쓰는 깃 명령어 정리

## branch 관련 명령어



### branch 보기
> git branch

> git branch -r (원격)

> git branch -a (모두)


### branch 생성
> git branch {branch name}


### branch 변경
> git checkout {pre-exist branch name}

> git checkout -b {new branch name} (새 브랜치 생성 및 변경)

### branch 삭제
> git branch -d {branch name}

> git branch -D {branch name} (merge 전일지라도 forced delete 수행)

### branch 이름 변경
> git branch -m {branch name} {new branch name}

### local branch remote 로 push
> git push origin {branch name} (--set-upstream config 설정을 따로 하면 위 command 를 생략가능) 

- - - 

## commit 관련 명령어

### 현재 git 상태 보기
> git status

### Stage File (stage 후 commit 으로 변경점 기록)
> git add (. ,file name, folder name -p모두 가능하다)

### Commit 하기
> git commit -m "message"

### Commit 이 불필요하게 너무 많아서 합치고 싶을때
> git rebase 

> git rebase -i cc2299ab

> git rebase -i HEAD~2 (이런식으로 commit 별 HEAD 나 ID 지정해서 합치는게 가능하다)

- - -

## 변경점 관리 명령어
### 변경점 버리기
> git restore
>
> git restore . 이런식으로 모든 변경점 버린다던가
 
### 변경점 commit 단위 변경
> git reset
>
> git reset --hard 이런식으로 commit 을 pure 한 상태로 돌리는것도 나쁘지않다.


> git reset --soft {commit id or HEAD} (변경사항 유지)
>
> git reset --hard {commit id or HEAD} (변경사항 버림)


### stash (변경점 저장)
> git stash
>
> 기본적으로 가장 편하지만 자주 context switching 을 하게 될 경우엔 추천하지 않음(뭘 어디까지 했는지 기억을 잘하면 상관 X)

> git stash push -m "wip in TestRepository" -u
>
> 이런식으로 뭐하던 작업인지 남겨두는게 좋다, -u 를 붙이면 새로 생긴 파일도 포함시켜준다. 

### stash 보기
> git stash list

> stash@{0}: WIP on master: cbcb911 initial commit 
> 
> stash@{1}: WIP on master: cbcb911 initial commit 

### stash 적용하기
> git stash apply {index}

### stash 버리기
> git stash drop {index}

### stash 적용 & 버리기
> git stash pop {index}
>
> 자주 적용해야할 파일을 stash 해두고 apply 로 자주 쓰는거 같다. 
> 그 외에 작업을 continue 할때엔 pop이 편하고.

- - -
## 병합 Merge
### Merge 하기
> git merge {branch}

> conflicts 가 나더라도
>
> git merge --abort(버림), git merge --continue(해결후 merge 진행) 을 적당히 써주면 된다.

- - -
## log 보기
> git log(리스트)
> 
> git show(최근)

- - -
## P.S.
### git reflog 및 검색하면 나오는 녀석들
> 소스트리나 kraken 이런걸 안쓰는 맛이라고 할까?
>
> bash 를 쓰면 이런 명령어를 요긴하게 쓸 일이 생길 수도 있다.
>
> 정말 멍청하게 stash 를 날린 직후라면? 써볼만 하다.
>
> 사라진 브랜치 or commit 은 reflog 로 쉽게 수습 가능하며
> 
>  ~~심지어 drop 한 stash 마저도 살릴수 있는 여지가 있다.~~
> 
> 참고 : [recover dropped stash](https://stackoverflow.com/questions/89332/how-to-recover-a-dropped-stash-in-git)
