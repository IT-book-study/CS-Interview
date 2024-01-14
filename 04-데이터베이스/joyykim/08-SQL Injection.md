# SQL Injection에 대해 설명해 주세요.
SQL Injection은 사용자로부터 입력받은 데이터를 직접 SQL 쿼리에 삽입하여 공격자가 의도한 악의적인 동작(SQL)을 수행하게 되는 보안 취약점.
주로 사용자의 입력 값에 대한 필터링 및 검증이 부족한 경우에 발생.

### 방지방법
1. Prepared Statements 및 Parameterized Queries (최고)
2. Stored Procedures 사용
3. ORM


- Prepared Statements 는 dbms 에서 미리 sql 구문을 파싱하고, 이후에 파라미터를 바인딩하여 쿼리하기 때문에 공격자의 입력값은 sql 구문으로 해석되지 않음.
- 또한 SQL 파싱을 미리 수행하여 쿼리 수행시간을 단축시킬 수 있음.
