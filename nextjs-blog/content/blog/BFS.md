---
title: "BFS 너비 우선 탐색 알고리즘"
date: "2025-05-03"
tags: ['Algorithm']
slug: "BFS"
description: "너비 우선 탐색(BFS, Breadth-First Search) 알고리즘은 그래프나 트리에서 특정 노드를 시작으로 인접한 노드들을 먼저 방문하는 탐색 알고리즘입니다."
---
![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/1f51a89b-82d4-4d76-83c9-efd3bd28e820/7d66ec30-2ade-4901-a536-dbbc56c8596d/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466WI3LTH7W%2F20250522%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20250522T091700Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBkaCXVzLXdlc3QtMiJGMEQCIHK5aiuXOrsmWBsfbJXoNHAfe1F1JrBXoQ5IYXp%2FPL4%2FAiBmetpgPtSC2AKaOKXlClU%2FRcp%2Btboe2e6%2B%2B8fPJF59DCqIBAjS%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMYG8JTL2X%2BmY9zG4hKtwDTse3WUJ7%2BBXocKSb68zIxtkqS7TiPnawJ1Y6HVh4jG7ne5lW6gciusXUALod0w0tNAYjasxK27xQFWHNqsrNYyCFi1FRZlbZyt0ENIGYnuVNeFPxnQ6YSjYPy5mF%2FYUJ37Nsol%2FTDsUeP68IYgLhPjlbgiw%2FEKbZYSOUq6kNXe%2BwMsneDaOq6vCLYhHSrkRtkybzi4PJ55UTRV9J4kmaIHOsiAD9BNFLd4i54SSquS4B%2BFN3sZ1darNts2VlrlQE%2BNdhXXl%2Bj%2BlmowVXnCdrSWRXtxViqvAmHhbLVMMsxd97EXgtj7Zc1dxC%2Fbd5ZSLtARNqlxQO71puAcg1vDa0Jxhfm0bDuyJiX1LEkzPIRCgYoTDUJSobq1YG51mEciZ6eDqS540xKQuu6pZz5H9f4eUYcszq4T3aqy2M6W21HBKVwo0mvW7fh%2BRzWpOgl%2FOtHkStaoUiX3rxxYF4axSGe%2BOM3OF4UnMRgcWXNhrQYjBRDJDDNBEduZzC7iVY7kRGc4H1W0uOdbxkR6Py0%2FRaAhMoW%2FIZU1GsG4oaHkcJ5zX%2F1Lhb3%2FQ9SAlogDQSyBgItCqGxX2DvbzR00ad5MMGuUDW7MvJ6BpCcCRHhVX85iEmK69wsu6BPKdpojcw48K7wQY6pgF2KPkyeAHHEQ07eOI3XMgbACverHS4Z9AZnH3W%2FfwDOU3XolMkx5DL47Ss7x6kPSkzs%2BCUfoAx9%2FiTQQr0gX2CdeXWqLBWtBpmjK1SWf5NUfT8BmvKvVWa60BnvVHGi7EOFc9mRUSLiFh3GfuKu8dm%2BBG6YloDNFmjkK7kse6lP0wWMxV0sUHEwHC9UqBnKvYOJxqon2w6srEKYAwwfSr6jtalT2dK&X-Amz-Signature=b797f8987e5845bf56d699cefc30c3ccbb8ab16b80dab852a48c7d782bbd21fe&X-Amz-SignedHeaders=host&x-id=GetObject)

## BFS 너비 우선 탐색 알고리즘이란?

너비 우선 탐색(BFS, Breadth-First Search) 알고리즘은 그래프나 트리에서 특정 노드를 시작으로 인접한 노드들을 먼저 방문하는 탐색 알고리즘입니다.

BFS는 주로 최단 경로 문제를 해결하는 데 사용되며, 큐(Queue) 자료구조를 이용해 구현합니다. 

### BFS의 특징
- **최단 경로 탐색**:
BFS는 최단 경로를 탐색하는데 유용합니다. 무방향 그래프에서 시작 노드로부터 모든 노드까지의 최단 경로를 찾을 수 있습니다.
- **FIFO(First-In-First-Out) 방식**:
큐 자료구조를 사용하여 구현되며, 먼저 들어온 노드가 먼저 처리됩니다.
- **방문 순서 보장**:
BFS는 같은 레벨의 노드를 먼저 방문하므로, 방문 순서를 보장합니다.
### BFS 알고리즘의 동작 원리
1. **시작 노드를 큐에 넣습니다.**
탐색을 시작할 노드를 큐에 삽입. 동시에 방문 여부를 확인하기 위해 시작 노드를 방문 표시합니다.
1. **큐에서 노드를 꺼내 인접한 노드들을 탐색합니다.**:
큐의 앞에서 노드를 꺼내어 그 노드에 인접한 모든 노드를 탐색합니다. 
인접한 노드들 중 방문하지 않은 노드를 큐에 삽입하고 방문 표시합니다.
1. **큐가 빌 때까지 반복합니다.**:
큐가 빌 때까지 위의 과정을 반복합니다. 큐가 비면 탐색이 종료됩니다.
## 백준 7576 토마토 문제
---
### BFS의 시간 복잡도
- **시간 복잡도**: O(V + E)
여기서 (V)는 그래프의 노드 수, (E)는 그래프의 간선 수를 의미합니다. 모든 노드와 간선을 한 번씩 탐색하므로 O(V + E)의 시간 복잡도를 가집니다.
### BFS의 구현 예제
다음은 BFS 알고리즘의 기본 구현 예제입니다:

```python
from collections import deque

def bfs(graph, start):
    # 모든 노드를 방문하지 않은 상태로 초기화
    visited = [False] * len(graph)
    # 방문할 노드를 저장할 큐 초기화
    queue = deque([start])
    # 시작 노드를 방문 표시
    visited[start] = True

    while queue:
        # 큐에서 노드를 꺼냄
        node = queue.popleft()
        print(node, end=" ")

        # 인접 노드를 방문
        for neighbor in graph[node]:
            if not visited[neighbor]: # 방문하지 않은 노드를
                queue.append(neighbor) # 큐에 삽입하고 
                visited[neighbor] = True # 방문 표시

# 예시 그래프 (인접 리스트)
graph = [
    [],          # 0번 노드 (사용되지 않음)
    [2, 3, 8],   # 1번 노드와 연결된 노드
    [1, 7],      # 2번 노드와 연결된 노드
    [1, 4, 5],   # 3번 노드와 연결된 노드
    [3, 5],      # 4번 노드와 연결된 노드
    [3, 4],      # 5번 노드와 연결된 노드
    [7],         # 6번 노드와 연결된 노드
    [2, 6, 8],   # 7번 노드와 연결된 노드
    [1, 7]       # 8번 노드와 연결된 노드
]

# 1번 노드에서 BFS 시작
bfs(graph, 1)

```
> BFS에서 사용하는 큐에 대한 정리 내용은 [Collections deque](/abe097c4c30e45859c99645f8a3a8178) 페이지를 참조
### BFS의 동작 과정
1. **시작 노드 방문**:
시작 노드(예: 1)를 방문하고 큐에 넣습니다.
  ```plain text
방문 순서: [1]
큐 상태: [1]

  ```
1. **노드 탐색**:
큐에서 노드 1을 꺼내고 인접한 노드 2, 3, 8을 큐에 넣습니다. 방문 표시를 합니다.
  ```plain text
방문 순서: [1]
큐 상태: [2, 3, 8]

  ```
1. **반복 탐색**:
노드 2를 꺼내고 인접한 노드 7을 큐에 넣습니다.
  ```plain text
방문 순서: [1, 2]
큐 상태: [3, 8, 7]

  ```
  노드 3을 꺼내고 인접한 노드 4, 5를 큐에 넣습니다.
  ```plain text
방문 순서: [1, 2, 3]
큐 상태: [8, 7, 4, 5]

  ```
  노드 8을 꺼내고 인접한 노드가 모두 방문되었으므로 큐 상태를 유지합니다.
  ```plain text
방문 순서: [1, 2, 3, 8]
큐 상태: [7, 4, 5]

  ```
  노드 7을 꺼내고 인접한 노드가 모두 방문되었으므로 큐 상태를 유지합니다.
  ```plain text
방문 순서: [1, 2, 3, 8, 7]
큐 상태: [4, 5]

  ```
  노드 4를 꺼내고 인접한 노드가 모두 방문되었으므로 큐 상태를 유지합니다.
  ```plain text
방문 순서: [1, 2, 3, 8, 7, 4]
큐 상태: [5]

  ```
  노드 5를 꺼내고 인접한 노드가 모두 방문되었으므로 큐가 비게 됩니다.
  ```plain text
방문 순서: [1, 2, 3, 8, 7, 4, 5]
큐 상태: []

  ```
### BFS의 사용 사례
- **최단 경로 탐색**:
무방향 그래프나 가중치가 동일한 그래프에서 시작 노드로부터 다른 모든 노드까지의 최단 경로를 찾을 때 사용됩니다.
- **레벨 탐색**:
트리 구조에서 각 레벨의 노드를 탐색할 때 사용됩니다. 예를 들어, 트리의 각 레벨을 한 줄씩 출력하는 문제를 해결할 수 있습니다.
- **맵 탐색**:
2차원 배열에서 시작점으로부터 모든 점까지의 최단 경로를 찾을 때 사용됩니다. 예를 들어, 미로 찾기 문제에서 BFS를 사용하여 출발점에서 도착점까지의 최단 경로를 찾을 수 있습니다.
BFS는 그래프 탐색 알고리즘 중 하나로, 너비 우선으로 탐색하여 최단 경로를 찾거나 각 노드의 레벨을 구할 때 매우 유용합니다. BFS의 핵심은 큐 자료구조를 사용하여 인접 노드를 순차적으로 탐색하는 데 있습니다.