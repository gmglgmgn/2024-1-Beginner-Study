# 지난주에서 추가

branch1에서 branch를 생성하면 새로운 branch는 branch1 에 매달리게 된다.

# 오늘 개괄

커밋 잘못했을 때 해당 커밋을 되돌릴 방법에 대해서 배워보자.

커밋의 변경, 되돌리기 시 git log 와 git status 명령으로 지금 우리의 상황을 잘 알고 수행하는 것이 중요하다.

## git log와 status
git log
	커밋 기록을 최신순으로 보여준다.
	--oneline 옵션으로 각 커밋을 한 줄에 요약해서 확인할 수 있다.
		맨 앞에 커밋 아이디가 등장한다.
		커밋 아이디는 변경, 되돌리기 할 커밋을 지정하는데 사용될 수 있다.
	HEAD 
		제일 최신 커밋에 위치한다. 
		(HEAD -> 현재브랜치) 형식으로 생겼음. 다음 커밋의 base 가 되는 commit 을 가리킨다.

git status
	상태는 트랙트와 언트랙트.
	언트랙트는 언모디파이드, 스테이지드, 모디파이드로 나뉨. - 1주차 정리를 참고하자.


## 되돌리기 3형제
#### commit --amend
커밋 어맨드
	마지막 커밋에서 뭔가 변경해야 할 때 사용.
		새로운 커밋으로 대체 됨. = 커밋 아이디가 변경 됨.
		디폴트 : vim에서 commit 메시지 수정함.
		-m 옵션으로 vim 진입 무시하고 커밋 메시지를 수정할 수 있다.
			git commit --amend -m 커밋 메시지
		--no-edit 옵션 = 메시지 수정 없이 커밋만 수정.
	주의사항
		내 브랜치 기반으로 누군가 작업 중인 경우, 무언가 엉켜 문제가 될 수 있다.
		어맨드는 나 혼자만 작업하는 경우 사용하자.

#### git reset
깃 리셋
	문제가 있는 커밋을 제거하고 싶을 때 사용
	3가지의 option이 있음. soft, mixed, hard 디폴트는 mixed reset.
		git reset --option commit_id
	체크 꼭 제대로 하고 넘어가자...
	각 옵션에 따라서 commit 삭제 후 commit의 내용을 어디로 가져올 것인지 결정 할 수 있다.
	soft = 커밋만 취소. commit 내용이 staging area로 돌아오게 됨.
	mixed = soft와 hard의 중간. commit의 내용이 working directory 로 돌아감. git add 부터 다시 해야한다.
	hard =	commit과 commit의 내용이 아예 증발함

#### git revert
리버트와 리셋의 차이?
	커밋 기록은 삭제되지 않고, 커밋 이전 상태로 덮어쓰는 새로운 커밋을 만든다.
	즉, B, A, C 순으로 커밋이 있는 경우 C를 revert 시키면, 
	A 커밋의 상태를 가지는 새로운 커밋 D 가 생성되는 것.

option
	디폴트 = --edit
		revert commit 생성 전에 commit 메시지를 수정할 수 있게 해주는 옵션. 디폴트 옵션임.
	--no-edit
		편집기 진입 없이 revet 를 완료할 수 있는 옵션.
	--no-commit
		revert 실행 시 commit 을 생성하지 않고, 되돌리려 하는 상태를 staging area에 올려줌.


# 느낀점
이번 주는 다른 일들로 좀 바빠서 아쉽게도 git 관련 공부를 많이 하지 못했다. 중간고사가 끝나면 한번 제대로 review 및 부족한 점을 채워야지.
지난 주 까지는 잘못된 commit은 어찌 처리하지? 같은 생각은 크게 하지 않았는데, 사실 꼭 필요한 기능이 아닐까 생각한다. commit은 항상 신중하게 해야한다고 배웠지만 그래도 사람이 실수하는 일이 언젠가 생길테니 말이다. 일단 그렇더라도 reset 은 좀 쓰기 무섭다.. commit 을 삭제한다는 것이 형상관리툴을 사용하는 목적에 위배되는 것 같기도 하고... 다만 merge 관련해서 오류가 생기거나 중구난방으로 관리하던 repo를 정리해야할 상황에는 어쩔 수 없이 사용해야 될 것 같기도 하다.
이번에 지난 시간 review를 하면서 branch를 어떤 branch에서 생성하는지에 따라 생성된 branch가 매달리는 곳이 달라진다는 것을 배웠다. 마치 트리구조 같구나.. 그래서 브랜치라고 부르나 보다. 소프트웨어를 개발한다고 치면, 메인은 기본으로 두고 각 기능은 main에 매달린 브랜치에서 작업, 관리하고, 해당 기능에 대한 추가 기능이나 큰 변경 사항이 생길 경우 해당 기능을 작업하던 브랜치에서 새로운 브랜치를 생성하여 작업하는 식으로 관리하면 편리할 것 같다.
