# CORS

**CORS (Cross-Origin Resource Sharing)**

* 리소스 호출이 허용된 출처를 서버가 명시해놓으면 출처가 다르더라도 통신할 수 있도록 만드는 정책
  * Origin(출처)는 스킴(프로토콜), 호스트(도메인), 포트 세가지로 정의된다
* CORS는 (자바스크립트)XHR/Fetch를 통해서 요청을 보낼 때 영향을 미친다

**동일 출처 정책 (Same-Origin Policy, SOP)**

* 동일한 출처 사이에서만 리소스를 공유하는 규칙의 보안정책
  * CSRF, XDD등의 공격으로부터 보호하기 위한 목적

**CORS 접근제어 시나리오**

**단순요청 (Simple Requests)**

![image-20230803163507952](C:%5CUsers%5Ciui47%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20230803163507952.png)

* 브라우저는 다른 출처로의 요청을 보낼 때 자동으로 HTTP 헤더에 Origin을 추가하여 보낸다 `Origin: https://foo.example`
* 응답을 받은 서버는 응답 헤더에 `Access-Control-Allow-Origin`을 실어 보낸다 이 헤더에는 허가된 출처 정보가 담겨있다
* **브라우저**는 요청의 Origin 헤더에 담긴 출처가 응답의 `Access-Control-Allow-Origin` 헤더에 있으면 해당 요청을 안전하다고 간주하고 응답을 가져온다 하지만 그렇지 않다면 해당 응답을 임의로 파기하고 자바스크립트로 응답의 내용을 전달하지 않는다

**단순 요청의 정보**

* `GET`, `POST`, `HEAD` 메서드만 허용
* `Accept`, `Accept-Language`, `Content-Language`, `Content-Type` 헤더만 허용
* `Content-Type`은 `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` 세가지만 허용

**프리플라이트 요청 (Preflight Requests)**

![image-20230803164005880](C:%5CUsers%5Ciui47%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20230803164005880.png)

* 실제 요청을 보내기 전에 사전 요청을 보내어 해당 리소스에 접근이 가능한지 먼저 확인하는 방식
  * OPTIONS 메서드를 이용한다
* _**이런 메소드와 헤더로 요청을 보낼건데, 너히 서버 CORS 정책에서 허용하는 요청이니?**_
  * 출처 Origin 헤더 추가
  * 요청메서드 `Access-Control-Request-Method` 헤더 추가
  *   요청 추가헤더목록 `Access-Control_request-Headers` 헤더추가

      ![image-20230803164357089](C:%5CUsers%5Ciui47%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20230803164357089.png)
* 응답 헤더들
  * `Access-Control-Allow-Origin` 허가된 출처목록
  * `Access-Control-Allow-Methods`서버측에서 허용하는 메서드 목록
  * `Access-Control-Allow-Headers` 허가 헤더 목록
  * `Access-Control-Max-Age` 캐시기간 ![image-20230803164644412](C:%5CUsers%5Ciui47%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20230803164644412.png)
* Preflight 요청이 필요한 이유는 무엇일까
  * CORS는 서버가 아닌 브라우저 구현 스펙에 포함된 정책
  * 서버는 CORS 위반 여부와 상관없이 요청을 처리하고 응답을 보낸다 응답을 받은 브라우저가 응답 헤더를 확인하고 응답의 파기 여부를 결정
  * `POST` `PUT` `DELETE` 같은 메서드는 서버에 부작용(side effect) 야기할 수 있다
  * 그러므로 미리 CORS를 위반하지 않았는지 조사할 목적으로 preflight 요청사용
  * 참고로 브라우저가 아닌 Postman 같은 API 테스팅 도구에서는 기본적으로 preflight를 보내지 않는다

**인증정보를 포함한 요청 (Credentialed Requests)**

* 쿠키, 토큰 같은 식별정보가 담긴 요청에 대해서는 더 엄격해진다
*   클라이언트는 요청을 보낼 때 credentials 옵션을 별도로 설정해줘야한다

    * fetch API은 다음과 같은 3가지 옵션이 존재
      1. `same-origin`: 같은 출처 간 요청에만 인증정보를 담는다
      2. `include` 모든 요청에 인증 정보를 담는다
      3. `omit` 모든 요청에 담지 않는다

    ![image-20230803165124758](C:%5CUsers%5Ciui47%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20230803165124758.png)

    * XMLHttpRequest 혹은 Axios는 `withCredentials` 옵션을 true로 설정
* 서버는 응답시 `Access-Control-Allow-Credentials` 헤더를 true로 설정 `Access-Control-Allow-Origin`은 와일드 카드가 될 수 없다

**JSONP**

**Access-Control-Allow-Origin**

**`@CrossOrigin`**
