# 16. Stateless와 Connectionless에 대해 설명해 주세요.

## Stateless

- Stateless는 서버가 **이전 요청의 상태**를 저장하지 않는다는 의미입니다.
    > stateless 프로토콜은 수신자가 이전 요청의 세션 상태를 저장하지 않는다. ([A stateless protocol is a communication protocol in which the receiver must not retain session state from previous requests.](https://en.wikipedia.org/wiki/Stateless_protocol))
- 대표적으로 HTTP가 Stateless한 프로토콜입니다.
- 이는 기본적으로 HTTP는 서버가 유저별 이전 요청들에 대한 데이터를 저장하는 방식을 제공하지 않는다는 의미입니다.

### 장점

- 확장성: 서버는 사용자 요청의 상태를 저장하고 추적하지 않아도 되기 때문에, 서버를 옆으로 확장하기 쉽습니다, 요청을 저장하고 추적해야 한다면 여러 서버에서 상태를 같이 관리해야 하기 때문에 불편할 것입니다.

### 단점

- 크기: 이전 상태를 저장하지 않기 때문에 클라이언트는 요청에 이전 상태를 포함해서 전송해야 합니다. 때문에 요청 메시지가 커질 수 있습니다.

### Q. Cookie는 Http를 Stateful하게 하지 않을까?

내 생각: 쿠키가 세션 관리로 쓰이는 것이지, 세션 관리를 강제하는 것은 아니기 때문에 http가 stateful하다고 하는 건 문제가 있어 보임 (헤더나 바디에 넣는 형식으로도로 세션 관리를 할 수 있다.)


## Connectionless

- Connectionless는 요청과 응답이 끝나면 연결을 유지하지 않는 방식입니다.
- 대표적이르 HTTP가 Connectionless한 프로토콜입니다.
- HTTP는 TCP 연결을 맺은 후에, 하나의 요청과 응답이 처리되면 TCP 연결을 바로 해제합니다.

### 장점

- HTTP에서 연결을 관리하지 않아도 되기 때문에 자원을 아낄 수 있습니다.

### 단점 

- 요청을 여러개 보내면, 연결을 수립하고 해제하는 오버헤드가 커집니다.

### 단점 해결 방안 - Keep-Alive

- Keep-Alive 커넥션을 맺으면 요청을 여러개 보낼때 다음 요청도 해당 연결을 재활용 합니다.
- HTTP 1.1부터 명시적으로 설정하지 않아도 암시적으로 설정됩니다.

