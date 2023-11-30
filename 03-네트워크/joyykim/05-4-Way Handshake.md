# 4-Way Handshake

3줄 요약
- TCP 는 연결지향 통신 프로토콜
- 연결을 맺고 끊는 과정이 필요
- 끊는 과정이 4-Way Handshake

4-Way Handshake 과정
- 송신 -> FYN -> 수신 (연결 끊자!)
- 송신 <- ACK <- 수신 (확인!)
- 송신 <- FYN <- 수신 (연결 끊자!)
- 송신 -> ACK -> 수신 (확인!)
