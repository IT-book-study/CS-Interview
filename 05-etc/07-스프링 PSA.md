# 스프링 PSA

- PSA 는 Portable Service Abstraction 의 약자로, AOP,IoC/DI 와 함께 스프링 프레임워크의 핵심 원칙 중 하나입니다.
- PSA 는 서비스 추상화를 이식 가능한 형태로 제공하는 개념입니다.
- PSA 를 통해 다양한 기술 스택/플랫폼을 추상화하여 어플리케이션 코드와의 호환성, 이식성을 높입니다!

스프링이 제공하는 몇가지 PSA 종류:

### Transaction PSA: 다양한 트랜잭션 관리 기술과의 통합을 위한 PSA
- JCBC(Java Database Connection)
- JTA(Java Transaction API)
- JPA(Java Persistence API)
- Hibernate
### Messaging PSA: 메시지 전송과 관련된 다양한 기술을 통합하기 위한 PSA
- JMS(Java Message Service)
- AMQP(Advanced Message Queuing Protocol)
### Caching PSA: 캐싱을 위한 PSA
- EhCache
- GemFire
- Redis
