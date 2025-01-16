// <br></br> : 한 줄 띄우기 필요할 때 복사해서 사용
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
