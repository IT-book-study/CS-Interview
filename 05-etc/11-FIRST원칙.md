# FIRST 원칙

클린코드의 저자인 밥 마틴이 제시한 규칙. 좋은 단위테스트를 만들기 위한 원칙을 설명한다.

- Fast: 유닛 테스트는 빨라야 한다.
- Isolated: 유닛 테스트는 그 자체만으로 실행되어야 한다. 즉, 독립적이어야 하고 다른 테스트에 의존하거나 영향을 주어선 안된다.
- Repeatable: 유닛 테스트는 반복 가능해야 한다. 테스트를 어디서 어떻게 몇 번을 진행하든 똑같은 결과가 나와야 한다. (멱등성)
- Self-validating: 유닛 테스트는 자체 검증이 가능해야 한다. 테스트 자체로 통과인지 실패인지 결과가 나와야 하며 이것은 자동적으로 이뤄져야 한다.
- Thorough:
  - should cover all the happy paths
  - try covering all the edge cases, where the author would feel the function would fail.
  - test for illegal arguments and variables.
  - test for security and other issues
  - test for large values, what would a large input do their program.
  - should try to cover every use case scenario and not just aim for 100% code coverage.

https://medium.com/@tasdikrahman/f-i-r-s-t-principles-of-testing-1a497acda8d6
