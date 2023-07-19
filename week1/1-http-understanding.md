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

- 클라이언트와 서버가 통신하기 위한 애플리케이션 레이어 프로토콜이다
- http를 이용하여 서로 하이퍼미디어 문서를 주고 받을 수 있다
  하이퍼미디어문서

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
