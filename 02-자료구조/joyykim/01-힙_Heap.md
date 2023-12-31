# 힙 (Heap)

## 요약
- 가장 높은 우선순위를 가지는 노드가 항상 root 위치에 오게 된다
  - 이 특징을 통해 우선순위큐를 구현할 수 있다
- 완전이진트리를 기반으로 하는 트리 자료구조 (이진힙)
- 최대힙, 최소힙으로 구분됨
- 중복된 값을 허용함
- 배열로 구현가능

## 힙의 활용
- 다익스트라 알고리즘
- 힙 정렬

## 조건
- 최대힙: 부모 노드가 자식 노드보다 커야함
- 최소힙: 자식 노드가 부모 노드보다 커야함
- 힙은 일종의 반정렬 상태(느슨한 정렬 상태)를 유지한다

# 연산
- 힙은 배열을 기반으로 구현됩니다. 각 노드의 인덱스 i에 대해, 왼쪽 자식은 2i, 오른쪽 자식은 2i+1, 부모는 i/2의 인덱스를 가집니다.
- 삽입: 새로운 원소를 힙에 추가합니다. 일반적으로 힙의 마지막 노드에 새로운 원소를 추가한 후, 힙의 성질을 만족하도록 재정렬합니다.
  - 삽입 재정렬(Heapify Up): (삽입된) 현재 노드와 부모 노드 비교, 부모보다 크다면 부모와 swap. root 까지 반복
- 삭제: root 의 최댓값 또는 최솟값을 삭제합니다. 삭제 후에는 힙의 성질을 유지하기 위해 재정렬 작업이 필요합니다.
  - 삭제 재정렬(Heapify Down): root 노드가 빠지고, 두 자식 노드를 비교해 큰 노드를 위로 올림. 올린 노드의 원래 위치의 두 자식 노드를 비교해서 큰 노드 올림. leaf 노드까지 반복
- 삽입/삭제의 재정렬 연산 시간복잡도는 힙의 높이에 의해 결정됨. 힙은 완전이진트리이므로 log n. 따라서 시간복잡도는 O(log n)
