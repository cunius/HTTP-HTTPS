# HTTPS

(HTTPS - SSL / SHTTP - SSH)

### 1. HTTPS - HyperText Transfer Protocol Secure

- HTTPS
    - HTTP + 암호화 + 증명서 + 안전성
    - HTTP의 보안 약점을 보완하기 위해 TCP/IP 위에 SSL/TLS 로 보안을 강화한 프로토콜 → 모든 HTTP 요청/응답은 암호화됨
    - HTTP’S’ - SSL (Secure Socket Layer) 약자
    - TLS (Transport Layer Security) - SSL v3.1 부터 이름 바껴서 발전함
    - TCP 의 연결이 이루어진 후 TLS를 통해 암호화 설정이 되고 통신함
- 특징
    - 443 Port, 웹에서 정보를 암호화하는 SSL/TLS 프로토콜로 세션 데이터 암호화
        - SSL/TLS 목표 - 기밀성, 데이터 무결성, 인증서 제공(ID, 디지털 인증서)
    - 웹 브라우저에서의 구현 정확도와 서버 소프트웨어, 지원하는 암호화 알고리즘에 따라 데이터의 보호 수준이 정해짐
    - 금융 정보, 메일 등 중요한 정보 주고받을 때 HTTPS 사용
- 장점
    - 보안이 강함 → 네트워크에서 열람, 수정이 불가능
    - SEO(Search Engine Optimization)에 유리
        - 동일한 키워드의 사이트에서 검색시 우선순위는 HTTPS 다음 HTTP
        - 검색 최적화를 위해 HTTPS 사용이 마케팅에서 유리
- 단점
    - 암호화 하는 과정에서 웹 서버가 부하됨
    - 설치 및 인증서 유지하는데 추가 비용 발생
    - HTTP에 비해 느리지만 요즘엔 별 차이 없음
    - 인터넷 연결이 끊긴 후 재인증 시간이 소요됨
        - 소켓 자체에서 인증을 하기 때문에 인터넷 연결이 끊기면 소켓도 끊어져서 다시 HTTPS 인증이 필요함
        - 소켓 - 데이터를 주고 받는 경로
        - HTTP - 비연결형 → 웹 페이지를 보다 인터넷 연결이 끊겼다가 다시 연결되어도 페이지를 계속 볼 수 있음

### 2. HTTPS 동작 방식

1. **클라이언트가 서버에 접속해 핸드쉐이킹 과정에서 서로 탐색**
    - Client Hello - 클라이언트가 서버에게 전송할 데이터
        - 브라우저마다 지원하는 암호화 알고리즘과 SSL 버전이 다르므로 해당 정보 전송
        - 클라이언트가 생성한 랜덤 데이터 전송
        - 클라이언트와 서버 사이 암호화 방식 통일을 위해 클라이언트가 사용할 수 있는 암호화 방식
        - 이미 Handshaking 기록이 있다면 자원 절약을 위해 기존 세션을 재활용하는 세션 아이디
    - Server Hello - Client Hello 에 대한 응답으로 전송할 데이터
        - 사용할 SSL 버전, 암호화 알고리즘, 서버가 생성한 랜덤 데이터 전송
        - 서버가 선택한 클라이언트의 암호화 방식
        - SSL 인증서
    - Certificate - Client 와 Server 인증 확인 / CA로부터 발급 받은 인증서 전송
        - Client 인증 확인
            - 서버로부터 받은 인증서가 CA에 의해 발급되었는지 본인이 가지고 있는 목록에서 확인 후 목록에 있으면 CA 공개키로 인증서 복호화
            - 클라이언트 서버 각각의 랜덤 데이터를 조합해 pre master secret 값 (데이터 송수신 시 대칭키 암호화에 사용할 키) 생성
            - pre master secret 값을 공개키 방식으오 서버에 전달 → 공개키는 서버로부터 받은 인증서에 포함
            - 일련의 과정을 거쳐 session key 생성
        - Server 인증 확인
            - 서버는 비공개키로 복호화해 pre master secret 값 취득 - 대칭키 공유 완료
            - 일련의 과정을 거쳐 session key 생성
    - Handshaking 종료
2. **데이터 전송**
    - 클라이언트와 서버가 Session Key로 데이터를 암호화/복호화 해 데이터 송수신
3. **연결종료 및 Session Key 폐기**

![Screenshot 2023-10-06 at 18.40.21.png](HTTPS%20cae3657c4e534a3e8acda38f14fd8983/Screenshot_2023-10-06_at_18.40.21.png)

---

- Session Key
    
    ![Screenshot 2023-10-17 at 20.04.23.png](HTTPS%20cae3657c4e534a3e8acda38f14fd8983/Screenshot_2023-10-17_at_20.04.23.png)
    

---

- references
    
    [[네트워크] HTTPS의 개념과 동작 원리](https://kimmeh1.tistory.com/499)
    
    [[Web] HTTP와 HTTPS의 개념 및 차이점](https://mangkyu.tistory.com/98)
    

---
