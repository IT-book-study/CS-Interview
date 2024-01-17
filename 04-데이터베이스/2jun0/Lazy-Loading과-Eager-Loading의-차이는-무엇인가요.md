# Lazy Loading과 Eager Loading의 차이는 무엇인가요?

orm 객체를 데이터 베이스에서 불러올때 연관된 객체를 로드하는 시점에서 차이가 있습니다.

- lazy loading: 연관 객체가 필요할때 로드하는 방식입니다.
- eager loading: 객체를 로드할때 연관 객체도 같이 로드합니다.
    - sqlalchemy에서는 join을 이용한 방식 / selectin을 이용한 방식 등이 있습니다.