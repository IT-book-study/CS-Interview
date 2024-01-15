# DB Join이 무엇인지 설명하고, 각각의 종류에 대해 설명해 주세요.

Join 은 관계형 데이터베이스에서 2개 이상의 테이블을 연결지어 데이터를 쿼리하고 표현하는 방법입니다.

종류
- INNER JOIN
- LEFT OUTER JOIN
- RIGHT OUTER JOIN
- FULL OUTER JOIN
- CROSS JOIN

조인 성능
- 최대한 필터링된 테이블을 기준으로 JOIN: 필터링된 결과를 기준으로 JOIN을 수행하면, JOIN 연산에 참여하는 행의 수가 줄어들어 전체 성능이 향상될 수 있음. WHERE 절 등을 사용하여 필터링된 테이블을 먼저 선택.
- 테이블 크기 고려: 작은 테이블을 기준으로 JOIN 하는 것이 더 좋음.
- 인덱스 활용: JOIN 조건에 사용되는 칼럼에 인덱스가 있는 경우, 해당 인덱스를 활용하여 먼저 필터링되도록 함. 이는 JOIN 연산에 사용되는 행의 수를 줄일 수 있음.
- INNER JOIN은 일반적으로 다른 JOIN 타입보다 빠르기 때문에 INNER JOIN을 먼저 수행하는 것이 좋음. LEFT JOIN, RIGHT JOIN, FULL JOIN 등의 JOIN 타입은 INNER JOIN 이후에 수행되도록 하자.
