# Transactional Outbox Pattern

### in-box & out-box
- in-box: 어플리케이션 외부에서 오는 요청을 DB inbox 테이블에 넣어놓고, task executor 가 inbox 테이블을 읽어서 요청을 처리하는 패턴.
- out-box: 어플리케이션 내부에서 외부 서비스로 보내야 하는 요청을 DB outbox 테이블에 넣어놓고, task executor 가 outbox 테이블을 읽어서 외부로 요청을 보내는 패턴.

### Transactional Outbox Pattern
문제:
- 어떻게 DB 트랜잭션과 메시지 전송(이벤트)을 원자적으로 할 수 있을까?
- 분산 서비스에서 메시지 브로커로 메시지를 전송해야 하고, DB 트랜잭션이 커밋이 되었을 때만 메시지가 전송된 것을 보장해야 한다.

해결:
- out-box 테이블을 생성한다. out-box 테이블은 외부에 전송할 메시지를 임시 저장하고 전송이력을 기록한다.
- 내부 비지니스 테이블에 수정 쿼리와 out-box 테이블 insert 쿼리를 트랜잭션으로 묶는다.
- 커밋이 되면 비지니스 테이블, out-box 테이블 모두 데이터 삽입/수정이 반영되었을 것이고, 롤백되었다면 out-box 에는 데이터가 없을 것이다. (원자성 보장)

message-relay 서비스가 out-box 테이블을 polling 해서 메시지 브로커에 전송하고 out-box 에 전송이력을 기록한다.


참고: https://microservices.io/patterns/data/transactional-outbox.html
