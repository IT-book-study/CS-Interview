# TCP와 UDP의 차이에 대해 설명해 주세요.

## 키워드

- 연결 지향성
- 3,4-way-hand-shake
- checksum

## 차이점

TCP는 연결 지향 전송 방식으로, 데이터를 전송하기 전에 3-way-hand-shake로 연결을 합니다.  
반면에 UDP는 비연결 지향 전송 방식으로, 연결 설정이 없으며, 신뢰성을 보장하지 않습니다. 그렇지만, 전송속도가 더 빠릅니다.

## 설명 안합니다. 질문 아래에 있는것 해주셔도 OK!

### TCP

- 연결: 3-way-hand-shake으로 syn(싱크) 패킷과 ack(어크) 패킷을 주고 받으며 연결을 설정합니다.
- 해제: 4-way-hand-shake로, fin(피니시) 패킷과 ack(어크) 패킷을 주고 받으며 연결을 해제합니다.
- 흐름제어: 서버와 클라이언트의 데이터 처리 속도를 해결하기 위한 제어
  - stop and wait: ack패킷을 받아야만 그 다음 패킷을 전송하는 방법
  - sliding window: 윈도우에 포함된 패킷들을 전송하고, ack패킷을 받으면 윈도우를 이동하는 방법
- 혼잡 제어: 네트워크 혼잡상황에 대비하는 방법
  - AIMD: 윈도우 크키를 하나씩 늘려보는 방법
  - Slow Start: 윈도우 크기를 지수 함수 꼴로 증가시키는 방법
- 패킷의 순서 번호를 붙임
- checksum: 패킷의 무결성을 보장하기 위한 방법
- 사용처: 데이터를 잘 받았는지에 대한 신뢰성이 필요한 서비스

### UDP

- checksum: 패킷의 무결성을 보장하기 위한 방법 (얘도 이건 있다!)
- 사용처: 데이터의 신뢰성은 중요하지 않고, 빠르게 받아야 하는 서비스

### 레퍼런스

- https://gyoogle.dev/blog/computer-science/network/%ED%9D%90%EB%A6%84%EC%A0%9C%EC%96%B4%20&%20%ED%98%BC%EC%9E%A1%EC%A0%9C%EC%96%B4.html
- https://cseweb.ucsd.edu/classes/sp15/cse123-a/lectures/123sp15-lec7.pdf
