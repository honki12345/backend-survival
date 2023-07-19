# 2. HTTP Client

## 목차

- TCP/IP 통신
- TCP와 UDP
- Socket과 Socket API 구분
- URI와 URL
- 호스트(host)
  - IP 주소
  - Domain name
  - DNS
- 포트(port)
- path(경로)
- Java text blocks
- Java InputStream과 OutputStream
- Java try-with-resources

---

### TCP/IP 통신

TCP/IP

- HTTP 통신은 TCP/IP를 통해 이루어진다
- TCP/IP는 TCP와 IP가 층을 이루는, 패킷 교환 네트워크 프로토콜의 집합이다

TCP 커넥션

- HTTP 메시지 전송을 위해서는 IP 주소와 포트번호를
이용해 클라이언트와 서버가 TCP/IP 커넥션을 맺어야한다
- HTTP 커넥션은 몇몇 사용규칙을 제외하고는 TCP 커넥션과 동일하다

---

### TCP와 UDP

TCP

- TCP는 두 개의 호스트를 연결하고 데이터 스트림을 교환하게 해주는 전송제어
계층의 프로토콜이다
- TCP는 데이터와 패킷이 보내진 순서대로 전달되는걸 보장한다

UDP

- UDP는 핸드셰이크로 연결설정을 하지 않고 데이터가 제대로 도착했는지 확인하지
않으므로 보안 및 안정성이 좋지 않다
- UDP는 대신 위의 프로세스를 거치지 않으므로 속도가 빠르다
- UDP 패킷을 데이터그램이다고 한다

---

### Socket과 Socket API 구분

Socket

- 네트워크에서 이름 및 주소를 지정할 수 있는 통신연결점(endpoint)이다

Socket API의 주요기능

- 연결 설정
- 데이터 주고 받기
- 연결 종료
