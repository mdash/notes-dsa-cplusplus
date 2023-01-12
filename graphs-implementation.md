### Data to be stored
- Sequence of vertices
- Sequence of edges
- Relationship between edges and vertices

### Edge list implementation
- List of vertices: E.g. [u, v, w, ...] (hash table)
- Edge list: E.g. [[u, v, a], [v, w, b], ...] where a and b are edge values
- If insert vertex - add to end of vertex list - amortized O(1)
- Remove vertex: O(1) to remove the vertex itself and total O(m) to remove all edges associated with the vertex
- areAdjacent: need to go through entire list of edges to check if 2 vertices are adjacent O(m) time
- incidentEdges: need to go through entire list of edges to check all edges that are incident to a given vertex, O(m) time

### Adjacency matrix
- Store vertex list, edge list and a matrix with pointer to each edge as shown below
![](assets/images/2023-01-12-17-41-23.png)
- Runtimes
    - InsertVertex: O(1) insert in the list, but add a row and column to the matrix as well - thus O(n) (need to add for each existing vertex)
    - RemoveVertex: same as above: O(n)
    - areAdjacent: extremely fast to index this: O(1)
    - incidentEdges: look at entire row and column for a vertex i.e. 2n checks - O(n)


### Adjacency list implementation
- Combining both the above
- Vertex list impl as hash table
- + include linked list pointing to the edges, edge list also links back to the vertices
- becomes a little messy
- Runtime
    - Insert: O(1)
    - removeVertex: O(deg(V)) - remove all the edges
    - areAdjacent: min (deg(V1), deg(V2)) - good runtime but not as good as adjacency matrix runtime
    - incidentEdges: deg(v)

### Summary
![](assets/images/2023-01-12-17-59-08.png)