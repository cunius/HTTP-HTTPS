# Cookie 🍪 Session

- 공통점 - 웹 통신간 유지하려는 로그인 정보 등의 정보를 저장하기 위해 사용
- 차이점 - 저장위치, 저장형식, 용량제한, 만료시점 등
    - 쿠키 - 개인 PC 에 저장됨
    - 세션 - 접속중인 웹 서버에 저장됨

### 1. Cookie

쿠키 = 웹 쿠키 = 브라우저 쿠키

- 쿠키
    - 웹 사이트가 사용자의 정보를 저장하기 위해 사용자의 pc, 스마트 폰, 태블릿 등 디바이스(클라이언트)에 키와 값들의 작은 데이터 조각을 저장하는 파일
    - 이름, 값, 만료날짜, 경로 등의 정보 저장
    - 일정 시간동안 데이터 저장 가능
    - 클라이언트의 상태 정보를 로컬에 저장하고 참조
    - 컴퓨터 내에서 프로그램처럼 실행될 수 없음
        - 바이러스 유포, 악성코드 설치 불가하지만 스파이웨어를 통해 유저의 브라우징 행동 추적 가능, 쿠키 탈취로 사용자의 웹 계정 접근권한 획득 가능
- 쿠키 구조
    - 이름
    - 값
    - 0개 이상의 속성 (이름, 값 쌍)
        - 속성: 쿠키의 만료 기간, 도메인, 플래그(Secure, HttpOnly) 등 정보를 저장
- 쿠키 종류
    - 세션 쿠키
        - 만료 날짜/시간을 지정하지 않음
        - 브라우저 메모리에 저장
        - 현재 세션이 끝나면 삭제됨
            - 브라우저 - 현재 세션이 끝니는 시점, 브라우저가 닫히면 세션 종료됨 / 브라우저 재시작 할 때 세션을 복원해 세션 쿠키가 무기한 존재할 수 있도록 함
    - 지속 쿠키
        - 만료 날짜/시간 지정
        - 파일로 저장 됨
        - 브라우저가 종료돼도 쿠키가 남아있음
        - Expires 속성에 명시된 날짜나 Max-Age 속성에 명시된 기간 이후에 삭제됨
- 쿠키  설정
    - Set-Cookie HTTP 헤더 사용해 설정하고 웹 서버의 HTTP 응답을 통해 송신됨
    - 헤더는 웹 브라우저가 쿠키를 저장하고 다음 서버 요청 시 송신할지 지시 → 브라우저는 쿠키가 미지원, 비활성일 경우 헤더 무시
    - 브라우저 내에서 실행되는 자바스크립트와 같은 스크립트 언어에 의해 설정될 수도 있음 → document.cookie
    
    ---
    
    ```html
    GET /index.html HTTP/1.1
    Host: www.example.org
    ...
    ```
    
    - 서버의 HTTP 응답에는 웹 사이트 홈페이지 내용이 포함됨 → 브라우저가 2개의 쿠키를 설정하도록 지시
    - 세션 쿠키 - 브라우저가 닫힐 때 브라우저에 의해 삭제되는 구조
- 쿠키 값
    - ‘**, / ; / 공백 문자**’를 제외한 인쇄 가능한 모든 ASCII 문자로 구성됨 (! 부터 ~, 유니코드 \u0021 부터 \u007E 까지)
- 쿠키 이름
    - ‘**= / 동일 문자**’는 이름과 값 사이를 구별하는 구분자 역할을 하므로 제외

### 2. Session

- 세션
    - 방문자가 웹 서버에 접속해 있는 상태를 하나의 단위로 보는 것
    - 일정 시간동안 같은 브라우저로(사용자)로부터 들어오는 요구를 하나의 상태로 보고 그 상태를 일정하게 유지시킴
    - 일정 시간 - 방문자가 웹 브라우저를 통해 웹 서버에 접속한 시점으로부터 웹 브라우저를 종료해 연결을 끝내는 시점
- 특징
    - 웹 서버에 웹 컨테이너의 상태를 유지하기 위한 정보 저장
    - 웹 서버에 저장되는 쿠키 = 세션 쿠키
    - 브라우저를 닫거나 서버에서 세션을 삭제했을 때만 세션이 삭제 됨 → 쿠키보다 보안이 좋음
    - 서버 용량 허용치만큼 저장 데이터에 제한 없음
    - 각 클라이언트의 고유 세션 아이디 부여 → 세션 아이디로 클라이언트를 구분해 각 클라이언트의 요구에 맞는 서비스 제공
- 세션 동작 순서
    
    웹 브라우저에서 페이지를 이동해도 로그인이 풀리지 않고 로그아웃 전까지 로그인 상태 유지
    
    - 클라이언트가 페이지 요청
    - 서버가 접근한 클라이언트의 Request Header 필드인 쿠키 확인 후 클라이언트가 해당 세션 아이디를 보냈는지 확인
    - 세션 아이디가 존재하지 않는다면 서버는 세션 아이디 생성 후 클라이언트에게 돌려줌
    - 쿠키를 사용해 서버가 클라이언트에게 돌려준 세션 아이디를 서버에 저장
        - 쿠키 이름: JSESSIONID
    - 클라이언트가 재접속 하면 JSESSIONID를 이용해 세션 아이디 값을 서버에 전달

### 3. Cookie vs Session

|  | Cookie | Session |
| --- | --- | --- |
| 저장 위치 | 클라이언트 (사용자 PC) | 웹 서버 |
| 저장 형식 | test | object |
| 만료 시점 | 쿠키 저장시 설정 - 브라우저가 종료되도 만료시점이 지나지 않으면 자동 삭제 안 됨 | 브라우저 종료시 삭제됨 - 기간 지정 가능 |
| 사용 리소스 | 클라이언트 | 웹 서버 |
| 용량 제한 | 300개 / 하나의 도메인 당 20개 / 하나의 쿠키 당 4KB(4096Byte) | 서버가 허용하는 한 무제한 용량 |
| 속도 | 세션보다 빠름 | 쿠키보다 느림 |
| 보안 | 세션보다 별로 | 쿠키보다 좋음 |

---

- ref
    
    [쿠키와 document.cookie](https://ko.javascript.info/cookie#ref-152)
    

---
