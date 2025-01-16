# linux_git

## git_commands.md 작성 요령

* #### 예시 코드를 제외한 모든 내용은 글머리 기호 뒤에 1칸 띄우고 작성 : 별표 사용
* #### 모든 인자는 <> 안에 작성   
* #### 형식
\* $ 명령 <인자> : 설명 -> 별표 뒤에 한 칸 띄우고 작성   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\* 옵션 <인자> : 설명-> 4칸 공백 넣어 들여쓰기 한 후 별표 넣고 한 칸 더 띄우고 작성   
예시코드 : " ```bash " 쓰고 예시코드 적은 후 다시 " ''' "로 닫기(공백, 별표 필요 없음)
* #### 예시
* $ git add <파일명 또는 디렉토리 주소> : 파일이나 디렉토리의 모든 파일을 staging area에 추가
  * -i, --interactive : 대화형 모드로 진입
  * -p, --patch : 파일의 일부분만 stage
```bash
$ git add patch
```   
* #### 같은 주제의 명령어는 한 뭉텅이로 작성
* #### 주제가 다른 명령어는 한 줄 띄우고 작성
