# Thread Safe 한 자료구조가 있을까요? 없다면, 어떻게 Thread Safe 하게 구성할 수 있을까요?

## 키워드

- Thread Safe
- 원자적 연산

## 요약

모든 연산이 Thread Safe한 자료구조를 묻는 것이라면, 대부분의 파이썬 자료구조는 그렇지 않은 것으로 알고 있습니다.

## 어떻게 하면 Thread Safe하게 구성할 수 있을까?

원자적 연산이 아닌 작업에 대해서 파이썬 threading모듈의 Lock을 사용하면 됩니다.

## 참고

[What kinds of global value mutation are thread-safe?](https://docs.python.org/3/faq/library.html#what-kinds-of-global-value-mutation-are-thread-safe)
