## HTTP Header

### **공통 헤더**

1. Date

   HTTP 메시지가 만들어진 시각이다. 자동으로 만들어진다.

2. Connection

   일반적으로 HTTP/1.1을 사용하며 Connection은 기본적으로 keep-alive로 되어있다.

3. Content-Length

   요청과 응답 메시지의 본문 크기를 바이트 단위로 표시해준다. 메시지 크기에 따라 자동으로 만들어진다.

4. Cache-Control

   요청과 응답 내의 캐싱 메커니즘을 위한 디렉티브를 정하기 위해 사용된다.

5. Content-Type

   컨텐츠의 타입(MIME)과 문자열 인코딩(utf-8 등등)을 명시할 수 있다.

6. Content-Language

   사용자 언어를 나타낸다.

7. Content-Encoding

   응답 컨텐츠를 br, gzip, deflate 등의 알고리즘으로 압축해서 보내면, 브라우저가 알아서 해제해서 사용한다.

</br>

### **요청 헤더**

1.  Host

    서버의 도메인 네임, Host 헤더는 반드시 하나가 존재해야 한다.

2.  User-Agent

    현재 사용자가 어떤 클라이언트(운영체제, 앱, 브라우저 등)를 통해 요청을 보냈는지 알 수 있다.

3.  Accept

    클라이언트가 허용할 수 있는 파일 형식(MIME TYPE)을 나타낸다.

4.  Cookie

    웹서버가 클라이언트에 쿠키를 저장해 놓았다면 해당 쿠키의 정보를 이름-값 쌍으로 웹서버에 전송한다.

5.  Origin

    POST같은 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지를 나타내는데 이때 보낸 주소와 받는 주소가 다르면 CORS 문제가 발생하기도 한다.

6.  If-Modified-Since

    페이지가 수정되었으면 최신 버전 페이지 요청을 위한 필드이다.

    만일 요청한 파일이 이 필드에 지정된 시간 이후로 변경되지 않았다면, 서버로부터 데이터를 전송받지 않는다.

7.  Authorization

    Authorization 헤더는 인증 토큰을 서버로 보낼 때 사용하는 헤더이다.

    API 요청같은 것을 할 때 토큰이 없으면 거절당하기 때문에 이 때, Authorization을 사용한다.

    JWT(Json Web Token) 을 사용한 인증에서 주로 사용 한다.

</br>

### **응답 헤더**

1.  Server

    웹서버 정보를 나타낸다.

2.  Access-Control-Allow-Origin

    요청 Host와 응답 Host가 다르면 CORS 에러가 발생하는데 서버에서 응답 메시지 Access-Control-Allow-Origin 헤더에 프론트 주소를 적어주면 에러가 발생하지 않는다.

3.  Allow

    Allow 헤더는 CORS 요청 외에도 적용된다.

4.  Content-Disposition

    응답 본문을 브라우저가 어떻게 표시해야 할지 알려준다.

5.  Location

    300번대 응답이나 201 Created 응답일 때 어느 페이지로 이동할지를 알려준다.

6.  Content-Security-Policy

    다른 외부 파일들을 불러오는 경우, 차단할 소스와 불러올 소스를 여기에 명시할 수 있다.

    하나의 웹 페이지는 다양한 외부 소스들을 불러온다. (이미지, JS, CSS, 폰트, 아이프레임 등)

</br>
</br>
</br>

출처: https://goddaehee.tistory.com/169 [갓대희의 작은공간]
