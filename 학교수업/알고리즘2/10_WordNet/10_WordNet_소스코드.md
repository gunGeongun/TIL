```python
def sap(g, aList, bList):    
    q = Queue()
    

    dist = {}  
    
    sapLength = float('inf')
    ancestor = None
    
    for v in aList:
        if v in bList:  # 동일한 정점이 양쪽 리스트에 있으면 바로 반환
            return v, 0
        q.put((v, True, 0))  # (vertex, from_a_list, distance) True면 aList에서 온거고 False면 bList에서 온것
        dist[(v, True)] = 0
    
    for v in bList:
        q.put((v, False, 0))  # (vertex, from_a_list, distance)
        dist[(v, False)] = 0
    
    while not q.empty():
        v, from_a, d = q.get()
        
        # 현재까지의 최단 거리보다 더 긴 경로는 무시
        if d >= sapLength:
            break
            
        # v의 모든 인접 정점에 대해
        for w in g.adj[v]:
            # w까지의 새로운 거리 계산
            new_dist = d + 1
            
            # 아직 방문하지 않은 정점이면 방문
            if (w, from_a) not in dist or dist[(w, from_a)] > new_dist:
                dist[(w, from_a)] = new_dist
                q.put((w, from_a, new_dist))
            
            # w가 반대편 리스트에서 이미 방문된 정점인지 확인
            # 방문되었다면 잠재적인 조상노드일 가능성 있음
            opposite_visited = (w, not from_a) in dist
            if opposite_visited:
                total_dist = new_dist + dist[(w, not from_a)] # 현재 탐색중인 경로에서서 w까지의 거리 + 반대편 리스트에서 w까지의 거리
                if total_dist < sapLength: #새로찾은 경로의 길이가 지금까지 탐색한 최단경로 보다 짧으면 업데이트 
                    sapLength = total_dist
                    ancestor = w
    
    if sapLength == float('inf'):
        return None
    
    return ancestor, sapLength
```