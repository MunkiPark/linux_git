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

  * 단축이름과 branch를 명시하지 않을 경우 origin 저장소의 master(main) branch를 다운로드
* $ git push <단축 이름> <branch> : 해당 remote repository의 해당 branch를 upstream 저장소에 업로드
  * 단축이름과 branch를 명시하지 않을 경우 origin 저장소의 master(main) branch에 업로드
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
   * --since, --until<기간> : 해당 기간 동안 생성된 commit만 출력(정확한 날짜, 상대적인 기간도 입력 가능)
   * --author <저자 이름> : 해당 저자의 commit만 출력
   * --grep <키워드> : 해당 키워드가 포함되 commit message를 가진 commit만 출력
   * -S <문자열> : 해당 문자열이 추가된 commit과 사라진 commit만 출력
   * -L <시작라인>,<끝라인>:<파일경로> : 해당 경로에서 시작라인부터 끝라인까지의 내용 변경 이력을 검색<br></br>
<!-- 여기까지--> 
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
* $ git checkout <tag 이름> : 해당 tag가 붙은 버전의 파일을 checkout
<!-- 여기까지-->
