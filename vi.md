<!-- <br></br> : 한 줄 띄우기 필요할 때 복사해서 사용--> 
* $ vi <파일명> : vi를 열어 해당 파일을 불러오기
  * 해당 파일이 없는 경우에는 빈 파일 생성

### <명령모드>
* 명령모드 → 입력모드
  * i : 현재 커서 자리부터 입력 시작(커서가 위치한 글자 앞부터 입력)
  * a : 현재 커서 다음 자리부터 입력 시작(커서가 위치한 글자 뒤부터 입력)
  * I : 현재 커서가 위치한 행의 제일 앞으로 이동하여 입력 시작
  * A : 현재 커서가 위치한 행의 제일 뒤로 이동하여 입력 시작
  * o : 현재 커서가 위치한 행의 다음 행으로 이동하여 입력 시작
  * O : 현재 커서가 위치한 행의 이전 행으로 이동하여 입력 시작
* 입력모드 → 명령모드 : esc<br></br>

* 커서 이동
  * h, j, k, l : 커서를 좌/하/상/우로 이동
  * ^, $ : 커서를 현재 행의 처음/마지막으로 이동(home/end도 사용 가능)
  * -, + : 커서를 이전/다음 행의 시작 위치로 이동
  * H, M, L : 커서를 화면의 맨 위/중간/맨 아래 행으로 이동
  * w, e : 커서를 다음 단어의 처음/마지막 글자로 이동
  * b : 커서를 앞 단어의 첫 글자로 이동
 
* 화면 이동
  * ctrl+u, ctrl+d : 반 화면 위/아래로 이동
  * ctrl+b, ctrl+f : 한 화면 위/아래로 이동(page up, page down도 사용 가능)
  * ctrl+y, ctrl+e : 화면을 한 행만큼 위/아래로 이동

* 특정 행으로 이동
  * G : 파일의 마지막 행으로 이동
  * <행번호> G : 지정한 번호의 행으로 이동

* 내용 수정
  * r : 커서가 위치한 한 글자 수정
  * cw : 커서 위치부터 현재 단어의 끝까지 수정
  * <n>cw : 커서 위치부터 n개의 단어 수정
  * s : 커서 위치부터 esc 입력할 때까지 수정
  * <n>s : 커서 위치부터 n개의 글자 수정
  * cc : 현재 행을 삭제하고 다시 작성
  * C : 커서 위치부터 행의 끝까지 수정

* 내용 삭제
  * x : 커서 위치의 글자 삭제
  * <n>x : 커서 위치부터 n개의 글자 삭제
  * dw : 커서  위치의 단어 삭제
  * <n>dw : 커서 위치부터 n개의 단어 삭제
  * dd : 커서 위치의 행 삭제
  * <n>dd : 커서 위치부터 n개의 행 삭제
  * D : 커서 위치부터 행의 끝까지 삭제

* 명령 취소
  * u : 명령 취소
  * U : 해당 행에서 실행한 모든 명령 취소
<!-- 여기까지--> 
