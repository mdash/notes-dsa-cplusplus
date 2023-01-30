### Traversal
- Visit every vertex and edge exactly once
    - Why?: To search for substructures
- Challenges
    - No natural ordering
    - No obvious start
    - Can loop
- Queue based BFS solution
    - Visit all adjacent nodes before visiting grandchildren
    - Visit vertices in the queue one by one and add their adjacent vertices to the queue when popping them out 
    - When an edge is visited the first time - it's called `discovery` and it's called `cross-edge` the next time (if it's already visited as an adjacent vertex of prior vertices that have been traversed)
    - Analysis
        - Runtime: O(n2) or O(n + m) [loop once for number of vertices and traverse all the nodes connected by edges, m may be n2 for fully connected graph]
    - Applications
        - Distance between 2 vertices (however, with BFS, one of the edges has to be the root node)
        - Following a cross-edge won't get us farther away from starting edge (since's it's already discovered by a parent/sibling vertex)
        - BFS discovery edges create spanning trees (spans across all edges in the entire graph)

- Stack based DFS (depth first search)
    - Can do through recursion 
    - A non-discovery edge is called Back-edge 
    - Same runtime: O(n + m)

### Minimum spanning trees
- A graph G' that is a spanning graph (connects all the nodes and no cycles) and has a minimum total weight among all spanning trees
- Kruskal's algo and Prim's algo

### Kruskal's algorithm
- Each edge has a weight (e.g. distance between nodes or time taken to travel the edge)
- Min-heap list of edges
- Disjoin set of all nodes in teh set
- Update the disjoint sets based on edges
    - Min-heap arranges from least cost to max cost edge, go down this list and do set union
    - If already in the disjoint set, don't add to the min spanning tree
