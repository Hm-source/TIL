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

<details>
<summary>2021.07.21</summary>
  <div markdown="3">
    <h2> sign up 구현 </h2>
    <h4> - SHAP_STORY/back_end/bin/</h4>
    <p> www.js 파일을 웹서버 실행파일로 변경.</p><br>
    <h4> - node.js 와 DB(mysql)연동하기 (db/database.js) </h4>
    <pre>npm install --save mysql</pre>
    을 통해 mysql 설치<br>
    <p> js파일에서 확잘 모듈 로딩 및 DB Connection 정보 설정 -> db/database.js에 있음.</p>
    <p>cmd 창에서 mysql을 실행하여 사용할 DB와 TABLE 생성.
    root계정에서 cmd창에서 mysql을 들어가는 과정에서 비밀번호 오류와 연동 오류 발생.</p>
    <ul>
            <li> 유형 1) ERROR 1045 (28000): Access denied for user 'root@'localhost' (using password: NO) </li>
            <li> 유형 2) Error: ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol requested by server; consider upgrading MySQL client</li>
    </ul>
    <p>MySQL 8부터 기본 인증 프로토콜이 기존의 mysql_native_password에서 caching_sha2_password로 변경되었고, 기존의 방식을 지원하지 않게 되서 발생한 문제라고 한다. 해결 방법으로는 1)비밀번호를 변경하거나 2)서버 설정을 변경한다. 참고사이트 : https://right-hot.tistory.com/entry/mysql-nodejs-%EC%97%B0%EB%8F%99-%EC%97%90%EB%9F%AC</p>
    <br>
    <h4> - sign up 구현에 필요한 모듈</h4>
    <p>npm을 이용하여 <br>
    "bcrypt", "body-parser", "cookie-parser", "cors", "ejs", "express", "express-session", "mysql", "node-mysql"<br> 설치</p><br>
    <h4> - ejs 사용</h4>
    <p> views/home 디렉토리를 만들어서 회원가입을 할 수 있도록 보여주는 ejs파일을 사용.</p>
    <p> <strong>* ejs란?</strong><br>EJS는 Embedded JavaScript의 약자로 Express에서 dynamic website를 만들기 위해 template으로 사용되는 파일(확장자 이름은 .ejs)
    </p>
    <p>app.js에 app setting</p><br>
    <pre>
app.set("views", "./views");<br>
app.set("view engine", "ejs");</pre><br>
    <h4> - app.js에 middleware 등록</h4>
    <pre>app.use(express.json());<br>
app.use(express.urlencoded({ extended: true }));</pre>
    body-parser의 일부기능이 express에 있어서 굳이 body-parser를 이용하지 않고 사용.<br>
    <h4> - 라우팅 모듈 사용</h4>
    <pre>const home = require("./routes/home");</pre>
    <p>\routes\home\home.ctrl.js 를 통해서 index.js 의 register 연결.
    <br> index.js에서 <pre>router.get('/register', ctrl.register);</pre>을 통해서 home.ctrl에서 내보낸 register 모듈을 연결.</p>
    <p>index.js 에서 라우트 경로 '/register'를 라우트 메소드 POST를 사용합니다. <br>이 메소드 안에서 sign up 페이지에서 입력한 아이디, 비밀번호, 이름, 학년 등을 query문을 통해서 mysql 'STORY'라는 db의 table USER에 INSERT합니다. </p><br>
    <p>비밀번호는 암호화가 필요하기 때문에 비밀번호 암호화 <strong>bcrypt hash 함수</strong>를 사용합니다. </p><br>
    <h3> 과제 </h3>
    <ul>
            <li> 게시판 구현하기 </li>
    </ul>
    <br>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 게시판, 마이페이지 관련 회의 및 merge</li>
    </ul>
  </div>
</details>

<details>
<summary>2021.07.24</summary>
  <div markdown="4">
    <h2> signin, signup merge 작업 </h2>
      <ul>
            <li> merge 중 오류 </li>
            <ol>
              <li>오타 수정</li>
              <li>[ERR_HTTP_HEADERS_SENT]: Cannot set headers after they are sent to the client 오류</li>
                <p>res.send를 없애니 오류 없어짐.</p>
            </ol>
    </ul>
    <h2> db table 변경</h2>
    <p>table 이름 변경 user -> student</p><br>
    <p>student phone_number(char(11)) 추가 </p><br>
    <p>CHARSET = utf8mb4 COLLATE = utf8mb4_general_ci 추가 -> Emoji (이모지😁) 를 지원</p><br>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 마이페이지, 게시판 구현 </li>
    </ul>
  </div>
</details>

<details>
<summary>2021.07.28</summary>
  <div markdown="5">
    <h2> 마이페이지, 게시판 관련 회의 </h2>
      <ul>
            <li> DB 재논의 </li>
            <li> 기능 논의</li>
            <li>버그 확인</li>
    </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 마이페이지, 게시판 기능 구현 및 오류 확인 </li>
    </ul>
  </div>
</details>

<details>
<summary>2021.08.04</summary>
  <div markdown="6">
    <h2> 마이페이지, 게시판 수정 회의 </h2>
      <ul>
            <li> routes 분리 </li>
            <li> 기능 확정 </li>
            <li> 버그 수정 완료</li>
    </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 마이페이지, 게시판 merge하기</li>
            <li> 버그 수정 </li>
            <li> react 코드 확인 </li>
    </ul>
  </div>
</details>

<details>
<summary>2021.08.11</summary>
  <div markdown="7">
    <h2> 마이페이지 관련 회의 </h2>
      <ul>
            <li> 버그 수정 완료 </li>
            <li> 개발 논의 </li>
      </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 메인페이지 react node.js 연결</li>
            <li> 로그인, 회원가입 react node.js 연결</li>
    </ul>
  </div>
</details>

<details>
<summary>2021.08.18</summary>
  <div markdown="7">
    <h2> 프론트엔드, 백엔드 합치기</h2>
      <ul>
            <li> 리액트 합치기 </li>
            <li> 개발 논의 </li>
      </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 로그인, 회원가입 react node.js 연결</li>
    </ul>
  </div>
</details>

<details>
<summary>2021.08.25</summary>
  <div markdown="7">
    <h2> signup, post 프런트, 백엔드 개발</h2>
      <ul>
            <li> 리액트 class, function, component 구현, backend 연결, db수정 </li>
            <li> 오류 고치기 </li>
      </ul>
    <h3> 다음 시간 할 일 </h3>
    <ul>
            <li> 회고록 작성 </li>
    </ul>
  </div>
</details>

<details>
<summary>개발 부분 및 프로젝트 회고록 작성(2021.08.27)</summary>
  <div markdown="7">
    <h2>프로젝트 소개</h2>
    <p>전래 동화와 함께하는 코딩 교육 웹 페이지</p>
    - 초등학교 4-6학년 학생을 대상으로 하는 전래 동화와 함께하는 코딩 교육 웹 페이지를 개발한다. <br>
    - 코딩 교육은 개미와 베짱이, 신데렐라, 견우와 직녀, 알라딘, 헨젤과 그레텔 등 유명한 전래 동화를 이용한 코딩 교육 콘텐츠를 제작한다.</br></br>
    <h2>팀원</h2>
    <ul>
            <a href='https://github.com/Hm-source/TIL'><li> 김효민 </li></a>
            <a href='https://github.com/bbjoite09'><li> 방희연 </li></a>
            <a href='https://github.com/sandwe'><li> 서현주 </li></a>
            <a href='https://github.com/chea-young'><li> 이채영 </li></a>
      </ul>
    <h2>개발 계획</h2>
    <ul>
            <li>  1주 차 : 콘텐츠 기획 및 프로토타입 제작(XD) </li>
            <li> 2주 차 : 서버 구축 및 DB 구축, UI/UX 구축</li>
            <li>  3주 차 : 서버, 웹 애플리케이션 세부 기능 사항 개발</li>
            <li> 4주 차 : 프로토타입 검증 - 1차 사전 TEST(*실제 초등학생 사용자 대상 TEST 예정) </li>
            <li>5주 차 : 추가 보완사항 논의</li>
            <li>6주 차 : 서버 및 웹 애플리케이션 추가 사항 수정</li>
            <li>7주 차 : TEST 및 발표 준비</li>
      </ul>
    <h2> 나의 개발 part</h2>
      <strong>Hm-source(김효민) 개발 part</strong><br>
      - Backend, 연결<br>
          - 회원가입<br>
          - 게시판<br>
      - Frontend<br>
          - 회원가입<br>
          - 게시판<br><br>
      <strong><h3>개발과정</h3></strong><h3>개발과정</h3>
      <ul>
            <li> 기본 웹페이지 구성요소 결정</li>
            <li> 템플릿 서치 및 템플릿 결정 / backend DB table 구성 (with 이채영) </li>
              <div>
              <ol> 
                <li>User, Post, BaseClass, HardClass, lessonrate 테이블 구성</li>  
                <li> 각 테이블 attribute 설정</li>
              </ol>
              </div>
            <li>node.js, ejs 회원가입 구현 및 라우팅</li>
            <p>- POST메소드, query문, bcrypt hash 함수 사용해서 회원가입 데이터가 db와 ejs로 전달되도록 구현</p>
            <li> signin, signup merge하고 db회의 통해서 db table 변경하고 mysql관련 오류 및 res.send관련 오류 수정</li>
            <li> 마이페이지, 게시판 기능 및 db 논의</li>
            <li> node.js, ejs 게시판 구현</li>
            <p>게시판 글쓰기, 게시판 상세페이지, 게시판 목록 구현</p>
            <li> react signup(회원가입) class 및 함수 구현</li>
            <li> react signup, node register를 연결</li>
            <li> react question(게시판) class 및 함수 구현</li>
            <li> react question, node posts 연결</li>
            <li> 게시판 오류 수정 </li>
      </ul><br>
    <h2><strong> - 회고(DAKI-(Drop, Add, Keep, Improve) ) - </strong></h2>
      <h4>- 개발 회고</h4>
    <ol>
        <li> Drop, 다음에는 이러지 마 </li>
        <div>
        <ul>
        <li>팀원들과 소통하기</li>
        <p>- 팀프로젝트가 엄청 많지도 않고 개발 부분에서 하나하나 이야기하기 힘든 부분들이 있다. 조금 더 자신감을 가지고 나에게 필요한 것, 나에게 요청한 것들에 대해서 말할 수 있는 능력을 키워야한다. 잘 몰라도 모르는 부분에 대해서도 스스로 빨리 공부하고 도움을 요청하고 서로 소통을 통해 해결해야한다. 더 지식을 쌓고 개발과정이 좀 더 잘 진행될 수 있도록 노력해야겠다. 기능 구현하는 부분에서 기한이 나에게 공부하고 하기에는 시간이 촉박해서 힘들었었는데 소통을 하며 해결하는 부분이 필요했던 것 같다.</p>
        <li>계획을 제대로 세워 기능 개발 및 기한에 대해서 모두 지키기</li>
        <p>- 처음 계획이 너무 간단하게 세운건지 몰라도 서로 이야기하기에도 계획이 부실했고 계획이 제대로 지켜지지 않았다. 이 부분에 대해서 확실히 짚고가야 문제가 생기지 않을 것 같다.</p>
        </ul>
        </div>
        <li> Add, 다음에는 이런 시도를 해보자 </li>
        <div>
        <ul>
        <li> 더 다양한 기능을 퀄리티 있게</li>
        <p>- 이채영 학생의 도움으로 데이터 흐름과 회원가입, 게시판 추가 등 여러 기능을 해낼 수 있었다. 하지만 게시판 구현 기능에서 제대로 구현되지 않은 부분들이 있었다. 회원가입에 대해서도 보안이나 권한 부분 등에 대해서도 자세하게 공부하고 진행하고 싶었다. 시간이 너무 촉박해서 처음 공부하는 입장에서 쉽지 않았다.더욱 공부해서 성공적이고 모두에게 편리하게 쓰일 수 있는 기능들을 구현하고 싶다.</p>
        </ul>
        </div>
        <li> Keep, 이대로만 잘해다오 </li>
        <div>
        <ul>
        <li>서로 과제를 내주고 서로 확인하는 과정</li>
        <p>- 기능 개발에서 서로 분량을 나누어 개발을 진행했다. 스터디 시간에는 과제를 체크하거나 오류를 수정하고 DB table회의를 진행했다. 과제로 진행해서 몸도 힘들고 밤새는 경우도 있었지만 스터디 시간 내에 같이 파트를 나누고 진행한 이채영학생에게 질문을 많이 하고 서로 이야기를 나누면서 성장할 수 있었다.</p>
        <li>잘 몰라도 구글과 친해지면서 공부하기</li>
        <p> - Node.js는 과제를 하며 많이 서치하는 과정을 거쳤다. 정말 탭이 작아질 정도로 많이 찾아보고 오류에 대해서도 많은 블로그, 교육용 사이트, youtube 등을 통해 공부하였다. 사실 처음 접하는 Node.js와 React에 대해서 처음에 접근하기 힘들었지만 지금도 많이 찾아보면서 많은 사례와 방법들을 익힐 수 있었다. </p>
        </ul>
        </div>
        <li> Improve, 이번에는 아쉬웠지만 다음에는 이렇게 해보자 </li>
        <div>
        <ul>
        <li> 기능 구현에서 짧은 기간 내에 한다는 압박감에 밤샘 작업이 많아서 효율적이지 못하는 상황이 발생했다.</li>
        <p>- 스트레스가 있어서 마지막 작업에서 좋은 효율이 나오지 않은 것 같다. 개발 기한에 대해서 고민해보고 시작해야한다. 갑자기 할 작업이 늘어난 것에 대해서는 내가 감당이 안되는 부분이 있어서 쉽지 않았다.</p>
        </ul>
        </div>
    </ol><br>
    <h4>- 전체적인 회고</h4>
    <ol>
        <li> Drop, 다음에는 이러지 마 </li>
        <div>
        <ul>
        <li>계획에 맞춰 진행하자.</li>
        <p>- 예상치 못한 사정이 있고 지치는 순간도 있었다. 계획이 틀어지는 순간 소통이 힘들어지고 피곤함이 쌓인다. </p>
        <li>빠른 도움 요청이 필요하다.</li>
        <p>- 각자 익숙하지 않고 모르는 부분이 많아서 모르는 부분에 대해서 말하기 쉽지않다. 서로 배려하는 부분을 줄이고 프로젝트를 우선으로 생각하고 혼자도 중요하지만 모두의 일이기 때문에 빠르게 도움을 요청하는 것이 좋다.</p>
        </ul>
        </div>
        <li> Add, 다음에는 이런 시도를 해보자 </li>
        <div>
        <ul>
        <li>기능 개발을 더욱 다양하게 해보고 싶다.</li>
          <p>- 기능을 제대로 완성하지는 못했지만 더 다양한 기능을 도전해보고 싶다.</p>
        <li>공부할 기간과 철저한 기한을 세우고 도전해야겠다.</li>
        <p>- node.js에 집중해서 공부할 예정이었지만 react도 사용하고 나서 react는 개발 기간이 짧았지만 더욱 궁금한게 많기에 더 철저한 계획을 가지고 공부하고 싶다.</p>
        </ul>
        </div>
        <li> Keep, 이대로만 잘해다오 </li>
        <div>
        <ul>
        <li>열심히 진행했다.</li>
        <p>- 각자에게 짧은 기간 또는 긴 기간이었겠지만 열심히 프로젝트를 진행했다. </p>
        <li>일단 도전해보았다.</li>
        <p>- 각자 익숙하지 않고 모르는 부분이 많아서 힘들었지만 도전했다는 것이 큰 의미가 있다. </p>
        </ul>
        </div>
        <li> Improve, 이번에는 아쉬웠지만 다음에는 이렇게 해보자 </li>
        <div>
        <ul>
        <li>전체적인 소통이 부족했다.</li>
        <p>- 혼자서 하는 것이 아니기 때문에 개발 계획을 잘 세우고 각 파트에서 맡은 부분을 서로 소통하면서 개발이 이루어져야한다. </p>
        </ul>
        </div>
    </ol>
  </div>
</details>