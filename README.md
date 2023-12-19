# URI/URL/URN

### 1. URI - Uniform Resource Identifier

- 통합 리소스 식별자
    - [google.com](http://google.com) / [https://www.google.com](https://www.google.com) 둘 다 가능
    - URL, URN 모두 포함
- 리소스 자체를 식별하는 고유한 문자열 시퀀스
    - Uniform: 리소스를 식별하는 통일된 방식
    - Resource: URI로 식별 가능한 모든 종류의 자원(웹 브라우저 파일, 그 외의 리소스 포함)
    - Identifier: 다른 항목과 구분하기 위해 필요한 정보

### 2. URL - Uniform Resource Locator

- 네트워크 상에서 통합 리소스의 위치를 나타내기 위한 규약, 웹 브라우저 주소
- 리소스 식별자와 위치를 동시에 보여줌
    - 웹 사이트 주소 + 컴퓨터 네트워크 상의 리소스
    - https://google.com
- 프로토콜 http, https, sftp, smp 등을 모두 나타내는 것
    - Protocol: 리소스에 접근하는 방법을 지정하는 방식
- 어떤 특정 서버에 있는 웹 문서를 가리킴

**URL 단축 서비스**

길이 제한이 있는 소셜 미디어에서 링크를 공유할 경우 URL을 단축함

기업의 경우 마케팅을 위해 쉽고 기억하기 쉬운 단축 URL 제공

→ Twitter - TinyURL을 사용해 긴 URL을 자동 변환

### 3. URN - Uniform Resource Name

- Path(경로)에 해당하는 부분
- 리소스 위치, 프로토콜, 호스트 등과 상관없이 각 리소스에 이름을 부여한 것
- 웹 문서의 물리적 위치와 상관 없이 웹 문서 자체를 나타냄
    - 웹 문서가 다른 웹 서버로 이동하거나 주소가 바뀌더라도 해당 문서를 찾을 수 있음

---

**Scheme**

- 리소스에 접근하는데 사용할 프로토콜
- http:// https://

**Host**

- 접근할 서버의 호스트 명
- www.google.com

**Path**

- 접근할 서버의 경로에 대한 상세 정보
- /mail/u/0/?ogbl#inbox

![Alt Screenshot 2023-10-04 at 03.13.20.png](URI%20URL%20URN%207eaa6e03c5ce4717a70dca6650564843/Screenshot_2023-10-04_at_03.13.20.png)
<img src="/path/to/img.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="Screenshot 2023-10-04 at 03.13.20.png"></img>
