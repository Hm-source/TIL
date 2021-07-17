# TIL ( 모각코 팀 이름 : SHAP_STORY)
  🔥TODAY I LEARNED 모각코_study🔥
<details>
<summary>2021.07.10</summary>
  <div markdown="1">
    <h2> 기본 웹 페이지 구성요소 </h2>
    <img src="https://user-images.githubusercontent.com/64147798/125152771-e2fe0700-e189-11eb-9f2a-b97a71482d8b.jpg"  width="600" height="370">
    <img src="https://user-images.githubusercontent.com/64147798/125152866-b4346080-e18a-11eb-8a89-b3c424dc73cd.jpg"  width="600" height="370">
    <img src="https://user-images.githubusercontent.com/64147798/125152870-bdbdc880-e18a-11eb-8736-155f20365f37.jpg"  width="600" height="370">
    <img src="https://user-images.githubusercontent.com/64147798/125152878-c8785d80-e18a-11eb-81fd-5bb822f70456.jpg"  width="600" height="370">
    <img src="https://user-images.githubusercontent.com/64147798/125152883-cf06d500-e18a-11eb-9769-1fc898c74491.jpg"  width="600" height="370">
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 웹페이지 템플릿 </li>
            <li> 회원가입, 로그인 구현 </li>
    </ul>
  </div>
</details>

<details>
<summary>2021.07.17</summary>
  <div markdown="2">
    <h2> 웹 화면 구성 </h2>
     <ul>
            <li> XD 템플릿 서치 공유 </li>
            <li> XD 템플릿 결정 </li>
     </ul>
    <h2> DB table 구성 </h2>
    <ol>
        <li> User(id(private key)(30), passwd(16), name, grade)</li>
          <ul>
            <li> id -> 사용자 아이디(PRIVATE KEY) </li>
            <li> passwd -> 사용자 비밀번호 (hash 단방향 사용)</li>
            <li> name -> 이름 </li>
            <li> grade -> 학년(초등학생 기준) </li>
            <li> 이메일 선택 기능 넣을수도</li>
          </ul>
        <li> POST(head, type, body, user, show boolean, index autoindex(private key)) </li>
      <ul>
            <li> index -> 게시물 순서(PRIVATE KEY) autoindex</li>
            <li> head -> 글 제목 </li>
            <li> type -> 글 분류 항목 </li>
            <li> body -> 글 내용 </li>
            <li> user -> 사용자 아이디 </li>
            <li> show -> 게시글 공개여부(boolean)</li>
          </ul>
        <li> BaseClass(index autoindex(private key))</li>
      <ul>
            <li> index -> 수업 인덱스(integer)(PRIVATE KEY) autoindex</li>
          </ul>
        <li> HardClass(index autoindex(private key))</li>
      <ul>
            <li> index -> 수업 인덱스(integer)(PRIVATE KEY) autoindex</li>
          </ul>
        <li> lesson rate(id(private key), complete(), class_num integer, level</li>
      <ul>
            <li> id -> 사용자 아이디(PRIVATE KEY) </li>
            <li> complete -> 완료 여부(boolean) </li>
            <li> class_num -> 수업인덱스 (integer)</li>
            <li> level -> base / hard</li>
          </ul>
    </ol>
    <strong>타입 표시하지 않은 것은 text이다.</strong>
    <h3> 과제 </h3>
    <ul>
            <li> 회원가입 구현 </li>
    </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 회원가입, 로그인 구현 확인 </li>
            <li> 마이페이지, 게시판 DB table 및 구현 </li>
    </ul>
  </div>
</details>


