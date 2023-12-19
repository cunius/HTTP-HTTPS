# TCP/IP

**Internet = TCP/IP 기반 네트워크 결합체**

| TCP
(Transmission Control Protocol) | 연결 지향(3-Way Handshake)
신뢰성 있음, 느림
문자 데이터 전송 |
| --- | --- |
| UDP
(User Datagram Protocol) | 비연결 지향(단방향)
신뢰성 낮음, 빠름
실시간 멀티미디어 데이터 전송 |

---

![Screenshot 2023-10-04 at 04.22.45.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.22.45.png)

### 1. OSI 7 Layers

- Application
    - User Interface 제공
    - UI를 통해 데이터 생성
    - HTTP, FTP, Telnet, SMTP, SNMP 등…
- Presentation
    - Encoding - 코드 변환 (부호화)
    - Compression - 압축
    - Encryption - 암호화
- Session
    - End-to-End 호스트 사이에서 application 연결 설정, 유지, 해지
- Transport
    - End-to-End 사이에 virtual circuit 설정, 유지, 해지
- Network
    - Routing - 최적 경로 결정
- Data Link
    - forwarding - 데이터 전달
    - error control - 오류 제어
    - media access control - 매체 접근 제어
        - LLC: Logical Link Control
        - MAC: Media Access Control
- Physical
    - 전기, 기계, 기능, 절차적 수단 제공

### 2. TCP/IP 4 Layers

- Application
- Transport
- Internet
- Network Access

### 3. TCP/IP Protocol Stack

![Screenshot 2023-10-04 at 04.24.35.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.24.35.png)

- DNS
    - 512 Byte 보다 클 때 TCP / 512 Byte 보다 작을 때 UDP

### 4. TCP Header

![Screenshot 2023-10-04 at 04.26.59.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.26.59.png)

- Header 뒤 Data는 있어도 되고 없어도 됨
- **Sequence number**: 데이터에 부착되는 고유 넘버
    - 증가 형태로 나오는 일련 번호
    - 출발 전에 미리 다 구할 수 있음
    - AN 가 그 다음 SN 로 사용됨
- **Acknowledgement number**: Sequence number + Data length
    - 데이터가 0 일때 → 제어 데이터 = 1
    - 받은 만큼 대답해서 데이터가 손실될 수도 있음 (AN 로 확인)
    - 데이터가 손실됐으면 제대로 받을 때 까지 계속 다시 보냄 → 신뢰성 체크
- HLEN: 기본 길이 20Byte + 옵션 최대 60Byte
- Flags
    - SYN (Synchronization) - 통신 시작시 세션 연결
    - ACK (Acknowledgement) - 송신측으로부터 패킷을 잘 받았다는 걸 알려줌
    - FIN (Finish) - 더이상 전송할 데이터가 없어 세션 연결 종료
    - RST (Reset) - 비정상적인 세션을 끊기위해 연결을 재설정
    - PSH (Push) - 버퍼링 없이 Application Layer의 응용프로그램으로 바로 전달
    - URG (Urgent) - 긴급 데이터의 우선순위를 높여 먼저 전달
- Window size
    - 흐름 제어 → 데이터 전송량을 조절해서 데이터를 좀 더 빨리 보냄
    - ACK 없이 연속해서 데이터 전송 가능
    - 수신 호스트 PC의 CPU 상태에 따라 처리
    - **window size = 0** 는 데이터 받을 만큼의 용량 없으니 보내도 못 받음

### 5. UDP Header

![Screenshot 2023-10-04 at 04.28.37.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.28.37.png)

- Data 전송을 위한 사전 프로세스 없음
- 빠르지만 신뢰성 없음

### 6. IP Header

![Screenshot 2023-10-04 at 04.29.53.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.29.53.png)

- 기본 길이 20Byte + 옵션 최대 60Byte
- Header 뒤 Data는 무조건 있어야 함, 값이 없으면 아무 값이나 넣음
- VER - IPv1~IPv6
    - IPv4: 가변 길이 → 항상 시작점 계산해서 위치 파악 (HLEN)
    - IPv6: 고정 길이 → 위치 파악할 필요 없음, 작업 과정 한 단계 줄임
- Total length = Header + Data 길이
- Service Type (Service Field)
    - TCP URG와 비슷

### 7. ICMP Header

![Screenshot 2023-10-04 at 04.34.17.png](TCP%20IP%20b03f6eaf51814da59d54b830eaa20579/Screenshot_2023-10-04_at_04.34.17.png)

- 총 8 Byte
- Error Reporting Message - IP 패킷 처리 도중 발생한 문제 보고
- Query Message - 네트워크 문제 진단, 다른 호스트로부터 특정 정보 획득
- IP Protocol - 송수신 시스템 사이 패킷을 최적 경로로 전달, 신뢰성 없고 비연결성 프로토콜
