# 균형이진탐색트리
- 일반적인 이진탐색트리는 worst case 시간복잡도가 O(n)이다.
- 균형이진탐색트리: 이런 단점을 극복하기 위해 삽입과 삭제가 일어날 때마다 편향이 일어나지 않도록 균형을 잡는 연산을 추가하여 이진탐색트리를 개선한 자료구조.
- 트리의 높이를 log n, 또는 그 근사치로 유지하는 것이 목표이다.
- Rotation(회전)을 통해 트리의 균형을 유지함.
- 대표적으로 AVL 트리, Red-Black 트리가 있다.

## AVL 트리
- 각 노드의 왼쪽 서브트리와 오른쪽 서브트리의 높이 차이(Balance Factor)가 항상 -1 또는 0 또는 1 이어야함
- 매우 빡세게 균형을 잡음

## Red-Black 트리
- 각 노드에 red 또는 black 을 할당하여 트리의 균형을 유지함

## 234트리
- Red-Black 트리와 유사

## Splay 트리
