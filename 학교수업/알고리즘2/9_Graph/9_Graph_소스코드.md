```python
class SCC:                                        # SCC(Strongly Connected Components) 클래스 정의
   def __init__(self, g):                        # 그래프 g를 입력받아 SCC를 초기화하는 생성자
       def recur(v):                            # 깊이 우선 탐색(DFS)을 수행하는 재귀 함수
           self.id[v] = self.count              # 현재 정점 v에 현재 SCC 번호(count)를 할당
           for w in g.adj[v]:                   # 현재 정점 v의 모든 인접 정점 w에 대해
               if self.id[w] < 0:               # 아직 방문하지 않은 정점이면 (id가 -1)
                   recur(w)                     # 해당 정점에 대해 재귀적으로 DFS 수행
                   
       topology_result = topologicalSort(g.reverse())  # 주어진 그래프를 뒤집은 후 위상 정렬 수행
       self.id = [-1 for _ in range(g.V)]      # 각 정점의 SCC 번호를 저장할 배열을 -1로 초기화
       self.count = 0                          # SCC 그룹의 개수를 카운트할 변수 초기화
       
       for v in topology_result:               # 위상 정렬된 순서대로 각 정점에 대해
           if self.id[v] < 0:                  # 아직 방문하지 않은 정점이면
               recur(v)                        # DFS 수행
               self.count += 1                 # 새로운 SCC 그룹을 찾았으므로 카운트 증가
   
   def connected(self, v, w):                  # 두 정점 v, w가 같은 SCC에 속하는지 확인하는 함수
       return self.id[v] == self.id[w]        # 두 정점의 SCC 번호가 같으면 True, 다르면 False 반환
```