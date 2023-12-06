# 11. DB Locking에 대해 설명해 주세요.

데이터베이스에서 Lock은 다수 트랜잭션이 동시에 데이터를 접근할때 생기는 문제를 해결하는 방법으로 쓰일 수 있습니다.  
대표적으로 Shared Lock과 Exclusive lock이 있습니다.

## Shared Lock

Shared Lock은 읽기 잠금으로, 어떤 데이터를 다른 트랜잭션에서 바로 읽을 수 있지만, 쓰는것은 대기해야 하는 잠금입니다.

## Exclusive Lock

Exclusive Lock은 쓰기 잠금으로, 데이터를 읽거나 쓰는 것 모두 대기해야 하는 잠금입니다.
