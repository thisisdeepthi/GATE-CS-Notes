# DS notes

## Types of edges in DFS

### Directed grpah

1. Tree - an edge which is present in the tree obtained after applying DFS 
2. Forward - an edge (u,v) is forward in which v appears after u
3. Back - an edge (u,v) is back in which v appears before u
4. Cross - in an edge (u,v) if v is neither ancestor or descendant of u 

### Undirected graph

1. Tree
2. Backward

## Kruskal algorithm for MST

- MST = a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.

- MST has (V-1) edges where V is the no of vertices

- Algo steps

```
1. Sort all the edges in non-decreasing order of their weight. 
2. Pick the smallest edge. Check if it forms a cycle with the spanning tree formed so far. If cycle is not formed, include this edge. Else, discard it. 
3. Repeat step#2 until there are (V-1) edges in the spanning tree.
```

- Number of possible MSTs increase, when we have multiple edges with same edge weights.