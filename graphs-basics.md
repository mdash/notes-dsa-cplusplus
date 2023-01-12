### Some interesting applications
- Graph coloring problem (e.g. exam scheduling for courses)
- Visualizing interconnected systems (e.g. internet visualization from 2003, course dependencies at university)

### Vocabulary
- Graphs usually denoted by `G` are a collection of Edges and Vertices (another term for Vertices: Nodes)
    - An edge is the connection between two vertices/nodes
    - number of vertices, `|V| = n`
    - number of edges, `|E| = m`
- An `instant edge` is an edge that's directly connected to a node
- A `degree` of a node is the number of instant edges
- `Adjacent vertices` are the nodes on the other side of the instant edges
- `Path(G)` is the sequence of vertices connected by edges
- `Cycle(G)` is the path with a common beginning and end vertex
- `Simple graphs` have no self-loops (node A-> node A connection) and multi-edges (multiple edges connecting node A-> node B)
- `Sub-graphs` are subsets of graph containing all the edges and vertices associated with a sub-set 
- If graphs don't share edges, they're disconnected

### Basic calculations
- Num of edges
    - Min for not connected: 0
    - Min for connected: $n - 1$
    - Max (simple graphs): $ n(n-1)/2$
- Degree of graph: $2m$ (double-count inbound as well as outbound edges)
