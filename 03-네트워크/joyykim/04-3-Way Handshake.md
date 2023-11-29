# 3-Way Handshake

3줄 요약
- TCP 는 연결지향 통신 프로토콜
- 연결을 맺고 끊는 과정이 필요
- 맺는 과정이 3-Way Handshake

개념
- TCP 헤더에는 Control Flag 가 있는데 이 안에 6개의 flag 가 있고 각 1bit 로 표현됨 (총 6bit)
- Control Flag 를 사용해 3/4-Way Handshake 가 동작됨
- flag 의 초기값은 0 이고 해당 flag 를 킬 때는 1 로 전송함 (SYN 전송 = SYN flag 를 1로 전송한다는 뜻)

3-Way Handshake 과정
- 송신 -> SYN -> 수신 (연결 맺자!)
- 송신 <- SYN+ACK <- 수신 (확인! + 연결 맺자!)
- 송신 -> ACK -> 수신 (확인!)
