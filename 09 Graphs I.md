# Intro to graphs
A node or a vertex (liet. viršūnė)

An edge connects 2 nodes (liet. briauna)

A path leads from node $a$ to node $b$ through connecting edges

A cycle is a path that begins and ends on the same node

A component is a connected part of a graph

[Practice problem](https://codeforces.com/problemset/problem/1944/A)

# Representation

- Adjacency list `vector<int> adj[N];`
- Adjacency matrix `int adj[N][N];`
- Edge list `vector<pair<int,int>> edges;`

# DFS & BFS
Open [Lithuanian book](https://siom.lmio.lt/m/t/knyga.pdf#page=95) for visual walkthrough

## Depth-first search (liet. paieška gilyn)
```cpp
vector<int> adj[N]; 
bool visited[N];

void dfs(int s) { 
	if (visited[s]) return; 
	visited[s] = true; 
	// process node s 
	for (auto u: adj[s]) 
	{ 
		dfs(u); 
	} 
}
```

## Breadth-first search (liet. paieška platyn)
```cpp
queue<int> q; 
bool visited[N];

visited[x] = true;
q.push(x); 
while (!q.empty()) { 
	int s = q.front(); q.pop(); 
	// process node s 
	for (auto u : adj[s]) { 
		if (visited[u]) continue; 
		visited[u] = true;
		q.push(u); 
	} 
}
```

[USACO dfs practice problem](https://usaco.org/index.php?page=viewproblem2&cpid=944)

# Neighbors and degrees

Degree of a node is the number of its neighbors.

The sum of degrees in a graph is always $2m$, where $m$ is the number of edges, because each edge increases the degree of exactly two nodes by one.

For Euler paths and cycles reference the Lithuanian book.

# Colorings 

In a coloring of a graph, each node is assigned a color so that no adjacent nodes have the same color. 

A graph is bipartite (liet. dvispalvis) if it is possible to color it using two colors. It turns out that a graph is bipartite exactly when it does not contain a cycle with an odd number of edges.

https://cses.fi/problemset/task/1668/

https://siom.lmio.lt/task/grafo_spalvinimas.html

# References
[Informatikos olimpiados: algoritmai ir taikymo pavyzdžiai](https://siom.lmio.lt/m/t/knyga.pdf#page=87)

[Competitive Programming Handbook](https://cses.fi/book/book.pdf#page=119)
