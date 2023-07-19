# 1. HTTP의 이해

## 목차

- HTTP(Hypertext Transfer Protocol)
- HTTP와 HTTPS의 차이(TLS)
- 클라이언트-서버 모델
- stateless와 stateful
- HTTP Cookie와 HTTP Session
- HTTP 메시지 구조
  - HTTP 요청(Request)와 응답(Response)
    - multipart/form-data
  - HTTP 요청 메서드(HTTP request methods)
    - 멱등성
  - HTTP 응답 상태 코드(HTTP response status code)
    - 리다이렉션

---

### HTTP(Hypertext Transfer Protocol)

정의

- World Wide Web에서 통신하는데 사용하는 프로토콜 프로그램이다.
- HTML 같은 하이퍼미디어 문서를 전송하기 위한 (OSI 7 계층 관점에서) 애플리케이션레이어 프로토콜이다.

### World Wide Web  

정의

- Internet을 통해 접근 가능한 (공용) 웹페이지의 상호연결 시스템

구성요소

- HTTP: 서버와 클라이언트 간의 데이터 전송 프로토콜
- URL/URI: 웹 요소에 접근하기 위한 식별자
- HTML: 웹 문서(요소)

### Internet  

정의

- TCP/IP(프로토콜 세트)을 사용하는 네트워크

---

### HTTPS

정의

- 보안 전송 계층을 통해 전송되는 HTTP이다.
- HTTP 하부에 전송레벨 보안 계층(SSL 또는 TLS)을 제공한다.

HTTP vs HTTPS

  HTTP는 암호화되지 않은 HTTP 메세지를 TCP를 통해 보낸다.
  HTTP: 네트워크 인터페이스 -> IP -> TCP -> HTTP
  HTTPS는 HTTP 메세지를 TCP로 보내기 전에 암호화하는 보안 계층으로 보낸다.
  HTTPS: 네트워크 인터페이스 -> IP -> TCP -> SSL/TLS -> HTTP

더 알아볼 것

- SSL와 HTTPS에서 이용되는 암호 인코딩 기법  
    키워드: 암호, 키, 대칭키 암호체계, 비대칭키 암호체계, 공개키 암호법, 디지털 서명, 디지털 인증서
- HTTPS 내부동작
  HTTPS스킴(SSL은 복잡한 바이너리 프로토콜) -> 보안전송셋업 -> SSL 핸드셰이크 -> 서버인증서/사이트인증서 검사
- 프락시와 HTTPS(보안)

---
