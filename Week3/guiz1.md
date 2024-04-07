## <p style="text-align:center;">개발 입문 스터디 Quiz 1</p>

#### Example
GDSC는 무엇의 약자인지 적으시오.

- 답: Google Developer Student Clubs

### Q1
Git에서 파일의 상태는 크게 untracked와 tracked로 나눌 수 있다.  
그렇다면 tracked에는 어떤 상태가 있는지 모두 적으시오.

- 답: unmodified, modified, staged

### Q2
Git에는 세 가지 영역이 있다.  
세 가지 영역을 모두 나열하시오.

- 답: working directory, staging area, local repository

### Q3
현재 우리는 ```main```브랜치에 있다.  
```develop```이라는 브랜치를 새로 만들고 이동까지 한번에 할 수 있는 명령어를 적으시오.

- 답: git checkout -b develop

### Q4
Working Directory에 있는 파일들을 모두 Staging Area에 추가할 수 있는 명령어를 적으시오.

- 답: git add .
- 단, pwd 가 working directory 인 경우 한정.

### Q5
```
1. Create a merge commit
2. Squash and merge
3. Rebase and merge
```
위의 세 가지가 어떤 차이가 있는지 간단히 적으시오.

- 답: 
	1. 브랜치에 있었던 commit 기록 유지, branch 에서의 commit 내용들이 합쳐져 새로운 커밋으로 main에 생성
	2. 브랜치에 있었던 commit 기록을 하나의 commit 으로 squash 하여 main 에 새로운 커밋을 추가.
	3. 브랜치에 있었던 commit 의 시점을, base를 main 으로 바꿈. commit id 가 변경되어 충돌의 가능성이 존재.


### Q6
```git log --oneline```으로 commit의 기록을 확인해보니  
첫 줄에 ```a1s2d3f (HEAD -> develop) docs: readme 추가```라는 log가 찍혔다.
알 수 있는 사실을 모두 적으시오.

- 답: 1. 현재 명령어를 사용한 branch는 develop 이다. 2. commit id 는 a1s2d3f 이다. 3. commit message는 docs: readme 추가 로, 해당 커밋으로 readme 라는 문서를 repository에 추가한 것으로 보인다. 4. 마지막으로 이루어진 commit 이 해당 커밋이다.

### Q7
```git log --oneline```으로 commit의 기록을 확인해보니 아래와 같은 log를 확인 할 수 있었다.  
```
a1s2d3f (HEAD -> develop) fifth commit
s2d3f4g fourth commit
345hj26 third commit
7g8dg7f second commit
5g568vk first commit
```
이때, fourth commit까지 제거하고 fourth commit과 fifth commit의 변경 사항은
Staging Area에 남아 있길 바란다면 reset을 어떤 옵션과 함께 사용하면 되는지 적으시오.

- 답: git reset --soft 345hj26

### Q8
```git log --oneline```으로 commit의 기록을 확인해보니 아래와 같은 log를 확인 할 수 있었다.
```
a1s2d3f (HEAD -> develop) fifth commit
s2d3f4g fourth commit
345hj26 third commit
7g8dg7f second commit
5g568vk first commit
```
reset은 너무 위험하니 revert를 사용하려고 하여 ```fifth commit```을 되돌리고 싶다면 
어떤 명령어를 사용하면 되는지 적으시오. 

- 답: git revert --no-edit a1s2d3f

### Q9
여러 사람이 협업하는 프로젝트에서 커밋을 되돌려야 한다.  
reset과 revert 중에 어떤 것을 선택할 것인지를 그 이유와 함께 적으시오.

- 답: reset은 commit 자체를 삭제하므로 위험하고 바람직하지 않다. 그러나 revert 는 새로운 커밋을 생성하여 처리하므로, 안전하고, 추후 개발 과정을 추적하기 훨씬 용이하다. 그러므로 나는 협업 시 reset 보다는 revert 명령을 이용하여 변경 사항을 되돌릴 것이다.
