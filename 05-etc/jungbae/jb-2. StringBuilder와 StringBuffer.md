StringBuilder, StringBuffer는 문자열을 처리하는데 사용되며 유사하고 차이점도 있습니다.

1. 공통점
- 우선 이 두가지의 차이점은 String과 달리 변할 수 있습니다. (mutable합니다.)
String은 한번 생성되면 할당된 메모리 공간이 변하지 않으며, + 연산자로 문자열을 붙이더라도 새로운 String객체를 만든 후 Heap영역에 등록됩니다. (가비지컬렉터가 회수)  
- StringBuffer/Builder는 객체 공간이 부족해지면 기존의 버퍼크기를 늘립니다.

2. 차이점
- StringBuffer 는 각 메서드별로 Synchronized 키워드가존재해 멀티스레드 환경에서 동기화를 지원합니다. 하지만 Builder는 지원하지 않습니다.
- 그렇기 때문에 단일스레드 환경이라면 StringBuilder가 성능이 더 좋을 수 있습니다.