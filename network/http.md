## HTTP 특징

1. 단방향성
   - 클라이언트가 서버로 요청을 보내고 이에 대한 응답을 받는 식으로 단방향적 통신
   - 서버가 클라이언트로 먼저 요청을 보낼 수 없다
2. 비연결성
   - 연결이 계속 유지되지 않고 `요청에 대한 응답이 끝나면 연결을 끊는다`(소켓 통신과 반대)
3. 무상태성
   - 클라이언트가 서버와 연결되어 있지 않아 기본적으로 상태를 가지지 않는다
   - 쿠키, 세션, 토큰 등을 사용한다

## **Connectless & Stateless**

HTTP는 Connectless 방식으로 작동

**서버에 연결하고, 요청해서 응답을 받으면 연결을 끊어버린다.**

기본적으로는 자원 하나에 대해서 하나의 연결을 만든다.

이런 작동방식은 각각 아래의 장점과 단점을 가진다

**장점 :**

불특정 다수를 대상으로 하는 서비스에 적합한 방식이다.

수십만명이 웹 서비스를 사용하더라도 접속유지는 최소한으로 할 수 있기 때문에, `더 많은 유저의 요청을 처리`할 수 있다.

**단점 :**

`연결을 끊어버리기 때문에, 클라이언트의 이전 상태를 알 수가 없다.` ⇒ _STATELESS_

이러한 HTTP의 특징을 stateless라고 하는데, Connectless로 부터 파생되는 특징이라고 할 수 있다.

클라이언트의 이전 상태 정보를 알 수 없게 되면, 웹 서비스를 하는데 당장에 문제가 생긴다.

클라이언트가 과거에 로그인을 성공하더라도 로그 정보를 유지할 수가 없다. HTTP는 cookie를 이용해서 이 문제를 해결하고 있다.

Cookie는 클라이언트와 서버의 상태 정보를 담고 있는 정보조각이다.

로그인을 예로 들자면, 클라이언트가 로그인에 성공하면,

서버는 로그인 정보를 자신의 데이터베이스에 저장하고 동일한 값을 cookie형태로 클라이언트에 보낸다.

첫 요청 시 :

**클라이언트 로그인 성공 then 서버 로그인정보를 자신의 DB에 저장**

(서버는 cookie를 키로하는 값을 데이터베이스에 저장하는 방식으로 "세션"을 유지한다)

**and then return 쿠키 to 클라이언트**

클라이언트는 다음 번 요청때 cookie를 서버에 보내는데,

서버는 cookie 값으로 자신의 데이터베이스를 조회해서 로그인 여부를 확인할 수 있다.

두번째 요청 시 :

**클라이언트 request(cookie) to server then 서버는 자신의 DB 조회 and then 로그인여부 확인**

## URI

- HTTP는 전송 프로토콜이고, URI는 자원의 위치를 알려주기 위한 프로토콜
- `World Wide Web 상에서 접근하고자 하는 자원의 위치를 나타내기 위해서` 사용한다.

## **Keep Alive**

HTTP 1.1 부터는 keep-alive 기능을 지원한다.

HTTP는 **`하나의 연결에 하나의 요청을 하는 것을 기준`**으로 설계가 됐다.

요즘 웹 서비스의 경우 간단한 페이지라고 해도 수십개의 데이터(문서, image, css, js)가 있기 마련인데, HTTP의 원래 규격대로라면 웹페이지를 하나 표시하기 위해서는

연결을 맺고 끝는 과정을 수십번을 반복해야 한다.

당연히 비효율적일 수 밖에 없다.

**연결을 맺고 끝는 것은 TCP 통신 과정에서 가장 많은 비용이 소비되는 작업**이기 때문이다.

예를들어 HTML로 표현된 문서를 다운로드 받는다고 가정해 보자.

이 문서에는 20개 정도의 image, css, js 파일이 있다.

**Keep alive를 지원하지 않을 경우** 모든 링크를 다운로드 할 때까지 반복한다.

Keep-alive 설정을 하면, 지정된 시간동안 연결을 끊지 않고 요청을 계속해서 보낼 수 있다.

웹 서버에 연결한다.

HTML 문서를 다운로드 한다.

Image, css, javascript 들을 다운로드 한다.

모든 문서를 다운로드 받았다면 연결을 끊는다.

---

- 출처

  - [HTTP 프로토콜이란?](https://shlee0882.tistory.com/107)

  - [[10분 테코톡] 🐬히로의 웹 요청과 응답](https://www.youtube.com/watch?v=xz7e-GL2g6g)

  - [[통신 방식] Http 통신과 Socket 통신 차이](https://mangkyu.tistory.com/48?category=762469)