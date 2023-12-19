# 대칭키/공개키/CA

### 1. 대칭키

- 암호화와 복호화에 쓰이는 키가 같은 암호화 알고리즘
- 클라이언트와 서버가 대칭키를 통해 통신을 하면 모두 공유키를 가지고 있어야 함
- 클라이언트는 보안 위험성이 높아 공유키가 노출될 수 있음, 공유키를 안전하게 서버에 전달하기 어려움

### 2. 공개키

- 공개키와 개인키를 함께 사용하는 암호화 알고리즘
- 암호화 - 공개키 사용 / 복호화 - 개인키 사용
- 클라이언트가 공개키로 암호화한 데이터를 서버에 보내면 서버는 해당 공개키로 암호화된 데이터를 복호화할 수 있는 개인키로 복호화 함
    - 안전하게 통신할 수 있지만 느림

### 3. CA - Certificate Authority

- SSL 적용을 위해 인증서가 필요함
- 인증서 - 서비스의 정보와 서버 측의 공개키가 포함됨
- CA - 인증서를 발급해주는 기업, 브라우저 - CA 리스트를 미리 가지고 있음
- 브라우저는 해당 CA가 리스트에 있는지 확인한 후 리스트에 있으면 해당 CA의 공개키로 인증서를 복호화 함
