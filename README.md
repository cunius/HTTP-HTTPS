# TCP 연결

- TCP 연결 관리
    - 3 Way Handshake: 가상 회선 설정
        - 클라이언트 연결 요구
        - 서버 응답 + 연결 요구
        - 서버 연결 요구에 대한 클라이언트의 최종 응답
    - TCP 데이터 전송
    - TCP 연결 종료
    
    ---
    

### 1. 3-Way Handshake

![Screenshot 2023-10-10 at 14.23.35.png](TCP%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%207b5ea24a607e46048a7e091c95261081/Screenshot_2023-10-10_at_14.23.35.png)

- Payload (위에서 밑으로 내려옴)

> SYN = 1
> 
> - 페이로드 되는 데이터 없음
> - 클라이언트가 서버에 패킷 보냄 → Destination port 중요

> SYN + ACK = 1
> 
> - SYN 에 대한 대답 + 서버가 클라이언트에게 패킷 보냄

> ACK
> 
> - 클라이언트가 서버에 대답
- 다음 SYN 는 SYN + ACK 의 ACK 가 그대로 내려옴
- 3 Way Handshake 가 끝나면 7계층 데이터가 나타남
- FTP, SSH, Telnet, HTTP, HTTPS가 데이터 보내면 TCP가 잘 받았다고 응답

### 2. 4-Way Handshake

![Screenshot 2023-10-10 at 16.57.54.png](TCP%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%207b5ea24a607e46048a7e091c95261081/Screenshot_2023-10-10_at_16.57.54.png)

- 연결 종료 → 항상 클라이언트가 요청
- CLOSE_WAIT 너무 오래 나오면 애플리케이션에 문제 있음
- ACK 가 중간에 끊기면 채널이 계속 열려있음 → ACK를 보냈다고 해도 바로 CLOSED 상태가 되진 않고 TIME_WAIT 동안 포트를 열어둠

### 3. netstat

네트워크 접속, 라우팅 테이블, 네트워크 인터페이스의 통계 정보를 보여주는 도구

- 옵션

| l | 연결 가능한 상태 |
| --- | --- |
| n | 포트 넘버 |
| t | TCP |
| u | UDP |
| p | PID / 프로그램 이름 |
| a | All |
| i | 이더넷 카드별 정상, 에러, 드랍 송수신 패킷 수 확인 |
| r | routing table |
| s | network 통계 |
- netstat 상태 값

| CLOSED | 포트가 닫혀있음 / 연결 종료 |
| --- | --- |
| CLOSING | 확인 메세지가 전송 도중 유실 |
| LISTEN | 서비스 하기 위해 포트를 엶
클라이언트의 접속 요청 대기 |
| ESTABLISHED | 응답이 오면 세션이 성립되어 통신이 이루어지고 있는 상태 |
| SYN_SENT | SYN 보낸 쪽
클라이언트가 서버에게 연결 요청 |
| SYN_RECEIVED | SYN 받은 쪽
(서버가 클라이언트로부터 SYN 받고 SYN + ACK 했지만 아직 클라이언트에게 ACK 받지 않음) |
| FIN_WAIT1 | 클라이언트가 서버에게 연결을 끊고자 요청
FIN 보낸 상태 |
| FIN_WAIT2 | 서버가 클라이언트의 연결 종료 응답을 대기
(서버가 클라이언트에게 최초로 FIN 받은 후 클라이언트에게 ACK 줬을 때) |
| CLOSE_WAIT | TCP 연결이 상위 응용프로그램 레벨로부터 연결 종료를 기다림 |
| LAST_ACK | 호스트가 원격지 호스트의 연결 종료 요청 승인을 대기 |
| TIME_WAIT | 연결이 종료됐지만 소켓을 열어놓은 상태, 시간 지나면 사라짐
FIN 받고 ACK 보냈지만 혹시 모를 불상사를 대비해서 기다림  |
| UNKNOWN | 소켓 상태 확인 불가 |
| SYN_RECV | 웹 서버 요청 연결 끊는 공격을 당했을 때의 대기상태
웹 서비스 지연, 서비스 자원 부족 문제 → hang 상태 됨 |

![Screenshot 2023-10-10 at 14.56.49.png](TCP%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%207b5ea24a607e46048a7e091c95261081/Screenshot_2023-10-10_at_14.56.49.png)
