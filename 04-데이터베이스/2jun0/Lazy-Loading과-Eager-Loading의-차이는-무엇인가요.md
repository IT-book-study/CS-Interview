# 연관관계 매핑과 Lazy loading / Eager loading

## 연관관계 매핑
- sqlalchemy에서 연관관계 객체를 매핑하기 위해선 `relationship()`과 `Mapped[연관 객체 타입]`타입힌트를 이용해 매핑합니다.

### One To One
- One To One 관계의 경우, 하나의 객체에만 외부키를 설정하고, 연관객체가 필요한 곳에 `relationship()` 필드를 설정합니다.
- `relationship(back_populates=연관 객체의 필드)`를 이용하면 연관객체 필드를 수정할때 연관객체의 필드도 수정(동기화)됩니다.

### One To Many / Many To One
- One To Many이나 Many To One 관계의 경우, One에 해당하는 객체의 경우 연관관계 객체가 필요하면 `Mapped[list[연관 객체 타입]]`타입힌트로 매핑 할 수 있습니다.

### Many To Many
- sqlalchemy는 관계 테이블을 직접 생성해주지 않습니다.
- 따라서 직접 관계 테이블을 생성한 뒤, 연결해야 합니다.
- 관계 테이블 객체를 생성하고 `relationship(secondary=관계 테이블)`을 쓰면 연관객체에 접근할때 자동으로 연관 테이블을 사용합니다.

## Lazy loading vs Eager Loading
orm 객체를 데이터 베이스에서 불러올때 연관된 객체를 로드하는 시점에서 차이가 있습니다.  
관계 필드를 생성할때 `relationship(lazy=옵션)`으로 여러 전략을 정할 수 있습니다.

- lazy loading: 연관 객체가 필요할때 로드하는 방식입니다.
    - `select`: 객체에 접근할때 
- eager loading: 객체를 로드할때 연관 객체도 같이 로드합니다.
    - `joined`: 객체를 로드할때 조인을 이용해 연관 객체를 불러옵니다.
    - `selectin`: 객체를 로드하고 난뒤 SELECT * FROM tb WHERE tb.f_id in () 구문으로 연관 객체들을 불러옵니다.
    
### 비동기 프로그래밍시 Lazy Loading

- 비동기 Session을 사용할때 Lazy Loading을 사용해 연관관계에 접근하면 Greenlet Error가 발생하기 때문에 주의해야 합니다.
- 이는 비동기 세션에서 동기로 I/O 처리를 할때 발생하는 오류입니다.
- `joined`을 이용하는 방법 / 쿼리를 작성할때 `selectinload(), joinedload()`옵션을 설정하는 방법으로 연관 객체까지 한번에 불러올 수 있습니다.
- 또는 ORM 모델 클래스에서 `AsyncAttr`믹스인을 상속해 awaitable한 연관객체를 만들수 있습니다.
