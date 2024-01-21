JPA에서도 다양한 락을 지원합니다. 특히 크게 낙관적, 비관적 락이 있습니다.  

1. 낙관적 락
낙관적 락은 데이터를 읽거나 수정하기 전에 충돌을 최소화하려고 시도하는 방식이며, 다수 트랜잭션이 데이터를 동시에 수정할 가능성이 낮을 것으로 예상될 때 사용됩니다. (유저의 정보변경)
@Version
private Long version;

이처럼 사용하며 낙관적 락을 사용하려면 버전이 있어야합니다. 트랜잭션을 커밋하는 시점에 충돌을 알 수 있다는 특징이 있습니다.  
엔티티에 버전속성을 추가하고, 각각의 트랜잭션이 엔티티를 수정할 때 버전이 자동으로 증가하도록 설정합니다. 버전 충돌이 발생하면 먼저 업데이트를 시도한 트랜잭션이 실패하게됩니다.  

EX)
@Service 클래스에서 업데이트 로직을 구현합니다.  
트랜잭션을 수행하며 트랜잭션 종료시 jpa는 버전을 자동 증가시킵니다. 다른 트랜잭션에서 이미 업데이트를 수행했다면 버전이 달라졌을 것이며, OptimisticLockException이 발생합니다.  


2. 비관적 락
비관적 락은 DB트랜잭션 락 메커니즘에 의존합니다. FORCE_INCREMENT를 제외하고는 버전은 사용하지 않습니다.   
Pessimistic_WIRTE, READ, FORCE_INCREMENT 모드를 사용합니다. (  Item item = entityManager.find(Item.class, itemId, LockModeType.PESSIMISTIC_WRITE)  )
메서드 안에 이런 방식으로 락을 획득하고 작업을 수행하며 트랜잭션 종료시 락이 해제됩니다. 동시에 데이터수정할 가능성이 높을 때 사용됩니다.  

- PESSIMISTIC_WIRTE
데이터베이스에 쓰기 락을 겁니다. select for update를 사용해 락을 겁니다. 이 락이 걸리면 그 레코드를 수정할때 다른 트랜잭션에서 읽거나 쓸 수 없습니다.  
- PESSIMISTIC_READ
데이터를 반복 읽기만 하고 수정하지 않는 용도로 락을걸때 사용됩니다.
lock in sharemode 혹은 for share를 사용해 읽기락을 걸고 쓰기작업을 수행된다면, 읽기가 끝날때까지 대기하게됩니다.
- PESSIMISTIC_FORCE_INCREMENT
버전정보를 사용합니다. 하이버네이트는 nowait를 지원하는 DB에대해 for update nowait옵션을 적용합니다.