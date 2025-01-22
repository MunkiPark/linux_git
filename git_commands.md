<!-- <br></br> : 한 줄 띄우기 필요할 때 복사해서 사용--> 
* $ git config --global user.name <이름> : 이름 등록
* $ git config --global user.email <이메일> : 이메일 등록
* $ git config --global core.editor <텍스트편집기> : 기본 텍스트 편집기 등록<br></br>
* $ git config --list : 현재 git 설정 출력<br></br>
* $ git help <명령> : 해당 명령에 대한 도움말 출력
  * -h, --help : 해당 명령의 옵션도 표시
* $ man git-<명령> : 해당 명령에 대한 도움말 출력<br></br>
* $ git init : 해당 directory를 git repository로 초기화(하위 directory .git을 추가)
* $ git clone <URL> <repository 이름> : URL의 저장소를 지정한 이름으로 clone
  * <repository 이름> 생략 가능 : 원본과 동일한 이름으로 clone<br></br>
* $ git status : 현재 git repository의 파일들의 상태 확인
  * -s, --short : 각 파일들의 변경 상태를 간단하게 표시<br></br>
* $ git add <파일명 또는 directory 주소> : 파일이나 directory의 모든 파일을 다음 commi에 추가(stage)
  * <파일명 또는 directory 주소> 대신 <.>을 적으면 해당 repository의 모든 파일을 추가
  * -i, --interactive : 대화형 모드로 진입
  * -p,--patch : 파일의 일부만 stage
* $ git diff : 수정 후 unstaged 상태인 파일과 수정 전의 staged 상태인 파일을 비교
  * <branch1>...<branch2> : 한 branch가 다른 branch의 조상이 아닐 때, 두 branch의 변경 내용을 비교
  * --staged, --cached : repository에 commit한 파일과 staging area의 파일을 비교
* $ git commit : staged 상태의 파일들을 commit
  * -v : commit msg에 diff 내용을 추가
  * -m <commit msg> : msg를 인라인으로 첨부
  * -a : 모든 tracked 파일들을 자동으로 staging area에 넣고 commit → stage 단계를 건너뛰고 commit 가능
  * -S : GPG 서명을 추가
* $ git rm <파일명> : working directory와 staging area에서 해당 tracked 파일을 삭제
  * -f : 이미 수정한 파일이나 staging area에 추가한 파일을 강제로 삭제
  * --cached : 파일을 staging area에서만 제거하고 working directory에서는 유지 → 추적 중지
  * -r : 디렉토리 삭제시 추가
* $ git mv <파일1> <파일2> : 파일1의 이름을 파일2로 변경(mv + git add )
* $ git remote : 현재 reopsitory에 등록된 remote repository의 단축 이름 표시
  * -v : remote reopository 이름과 URL을 같이 표시
* $ git remote add <단축 이름> <URL> : 해당 URL의 remote repository를 지정된 단축 이름으로 추가
* $ git fetch <단축 이름> <branch> : 해당 remote repository의 해당 branch에서 데이터 다운로드
  * 단축이름과 branch를 명시하지 않을 경우 origin 저장소의 master(main) branch를 다운로드
* $ git pull <단축 이름> <branch> : 해당 remote reopsitory의 해당 branch에서 데이터를 다운로드받아 자동으로 merge
  * --rebase : merge대신 rebase 실행

  * 단축이름과 branch를 명시하지 않을 경우 origin 저장소의 master(main) branch를 다운로드
* $ git push <단축 이름> <branch> : 해당 remote repository의 해당 branch를 upstream 저장소에 업로드
  * 단축이름과 branch를 명시하지 않을 경우 origin 저장소의 master(main) branch에 업로드
  * :<바꿀 remote branch명> 추가 : 해당 이름으로 바꾸어 push
  * --delete <remote branch> : 해당 remote branch 삭제
* $ git remote show <단축 이름> : 해당 repository의 정보 출력
* $ git remote rename <기존 단축 이름> <바꿀 단축 이름> : remote repository의 이름을 변경
* $ git remote rm <단축 이름> : 해당 remote repository를 삭제<br></br>

* $ git log : 현재 repository의 히스토리를 가장 최근 commit부터 출력
  * <시작 commit>..<마지막 commit> : 지정한 commit 범위의 히스토리만 출력
  * -p, --patch : 각 commit의 diff 결과를 출력
  * -<n> : 최근 n개의 commit만 출력
  * --stat : 각 commit의 통계 정보(수정된 파일, 변경된 라인 수, 요약)를 출력
  * --not : 현재 branch의 commit 중 master branch에 없는 commit들의 정보만 출력
  * --abbrev-commit : 짧고 중복되지 않는 hash를 출력(기본 7자, 중복될 경우 증가)
  * -g : reflog를 출력
  * -G <정규표현식> : 해당 정규표현식 패턴이 포함된 commit을 검색
  * --pretty=<인자> : 인자에 따른 형식으로 히스토리를 출력
    * oneline : 각 commit을 한 줄로 출력
    * format:"<포맷>" : 자신만의 포맷을 적어 히스토리를 출력
      |옵션|설명|옵션|설명|옵션|설명|
      |-|---|-|---|-|---|
      |%H|commit hash|%p|짧은 길이 부모 hash|%cn|commiter 이름|
      |%h|짧은 길이 commit hash|%an|저자 이름|%ce|commiter mail|
      |%T|tree hash|%ae|저자 mail|%cd|commiter 시각|
      |%t|짧은 길이 tree hash|%ad|저자 시각(--date옵션 참고)|%cr|commiter 상대적 시각|
      |%P|부모 hash|%ar|저자 상대적 시각|%s|요약|
   * --graph : branch와 merge 히스토리를 보여주는 아스키 그래프 출력
   * --decorate : branch 이름을 표시
   * --all : 모든 branch를 표시
   * --since, --until<기간> : 해당 기간 동안 생성된 commit만 출력(정확한 날짜, 상대적인 기간도 입력 가능)
   * --author <저자 이름> : 해당 저자의 commit만 출력
   * --grep <키워드> : 해당 키워드가 포함되 commit message를 가진 commit만 출력
   * -S <문자열> : 해당 문자열이 추가된 commit과 사라진 commit만 출력
   * -L <시작라인>,<끝라인>:<파일경로> : 해당 경로에서 시작라인부터 끝라인까지의 내용 변경 이력을 검색<br></br>
 
* $ git tag <tag 이름> <commit checksum> : 해당 이름으로 주어진 checksum의 commit에 lightweight tag 생성
  * commit checksum을 명시하지 않을 경우 현재 commit에 대해 tag 생성
  * tag 이름과 commit checksum을 모두 명시하지 않으면 이미 해당 repository에 만들어져있는 tag 목록을 출력
  * -a : annotated tag로 생성(tag 이름 앞에 작성)
  * -d <tag 이름> : 지정한 tag를 삭제
  * -m : tag message를 추가
  * -s : GPG 서명을 추가
  * -l <키워드>, --list <키워드> : 해당 키워드를 포함하는 tag만 출력(tag 조회할 때만)
  * -v <tag 이름> : 지정한 tag의 서명, 정보 표시(tag 조회할 때만)
* $ git push <remote repository> <tag 이름> : 해당 remote repository에 해당 tag를 push
  * --tags : local repository의 tag 중 remote server에 없는 tag들을 모두 push
* $ git checkout <tag 이름> : 해당 tag가 붙은 버전의 파일을 checkout<br></br>
<!-- 여기까지-->
* $ git branch <branch명> : 해당 이름으로 새로운 branch 생성
  * branch명을 명시하지 않을 경우 현재 branch 목록 출력
  * -d <branch> : 해당 branch를 삭제(merge하지 않은 커밋을 가진 branch는 삭제 불가>
  * -D <branch> : merge하지 않은 branch를 강제 삭제
  * -v : 각 branch의 마지막 commit message 출력
  * -vv : 각 branch의 추적 상황 표시(마지막 fetch시점 기준>
  * --merged : 이미 merge한 branch만 표시
  * --no-merged : merge 안 된 branch만 표시
* $ git checkout <branch> : 해당 branch로 이동
  * -b <branch명> : 해당 branch명으로 새로운 branch를 생성한 후 이동
  * --track <remote repository>/<remote branch> : 해당 remote branch의 tracking branch 생성
* $ git merge <branch> : 해당 branch를 현재 위치한(HEAD가 가리키는) branch에 merge
  * -S : merge commit에 GPG 서명 작성
  * -abort : merge를 취소하고 merge하기 전으로 복구
  * --verify-signature : 신뢰할 수 있는 사람이 서명한 commit만 merge
  * -Xignore-all-space : 모든 공백을 무시하고 merge
  * -Xignore-space-change : 뭉쳐 있는 공백을 하나로 취급<br></br>
* $ git ls-remote <remote  repository> : 해당 remote repository의 모든 Refs(branch, tag등) 출력
* $ git rebase <base branch> <topic branch> : topic branch를 base branch에 rebase
  * topic branch를 명시하지 않을 경우 현재 branch를 base branch에 rebase
  * onto <branch1> <branch2> <branch3> : branch2가 branch1에서 갈라져 나오고 branch3이 branch2에서 갈라져 나왔을 때, branch3 고유의 commit만 branch1에 rebase
<!-- 여기까지-->
* $ git reflog : reflog를 표시<br></br>
* $ git stash : 현재 작업물을 stash에 저장
  * --keep-index : 이미 stagingarea에 들어있는 파일을 제외하고 저장
  * -u, --include-untracked : untracked 파일도 저장
  * --patch: 대화형 프롬프트를 통해 원하는 데이터만 저장
  * -all : 모든 파일을 저장
* $ git stash list : 저장한 stash를 확인
* $ git stash apply <stash 이름> : 지정한 stash를 현재 branch에 적용
  * <stash 이름>을 명시하지 않을 경우, 가장 최근의 stash를 적용
  * --index : stash를 적용하면서 staged 상태로 변경
* $ git stash drop <stash 이름> : 해당 stash를 제거
* $ git stash pop <stash 이름> : 해당 stash를 적용한 후 제거(stack의 pop과 동일)
* $ git stash branch <branch 이름> : stash할 당시의 commit을 checkout한 후 새로운 branch를 만들고 적용(정상적으로 적용되면 stash를 삭제)<br></br>
* $ git clean : working directory의 파일들을 삭제
  * -f : 강제로 삭제
  * -d : directory 삭제 시 필요
  * -n : 가상으로 삭제한 후 어떤 파일들이 삭제되는지 표시
  * -x : .gitignore에 명시되어 commit할 때 무시되는 파일들도 삭제
  * -i : 대화형 프롬프트를 이용하여 삭제
<!-- 여기까지-->
