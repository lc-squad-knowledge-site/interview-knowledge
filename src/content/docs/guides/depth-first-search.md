---
title: Depth First Search
description: A guide in my new Starlight docs site.
---
DFS finds the the inorder first path in a graph from a source vertex to each vertex. DFS will alsp find the shortest path in a tree, but not general graphs.

Works in $O(n + m)$ time where `n` is the number of vertices and `m` is the number of edges.

The idea behind the algorithm is to go ass deep into the graph as possible, and backtrack onve we hit a vertex without any unvisted adjacent vertices.

1.  Vertex (or Node): A fundamental unit of a graph, representing a point or an entity in the graph.
2.  Edge: A connection between two vertices that represents a relationship or interaction between them.
3. Tree Edge - refers to an edge that is part of a tree, which is a connected, undirected graph without any cycles.
- A tree edge connects two vertices (nodes) in the tree, and each pair of vertices is connected by exactly one path. Tree edges are important in various algorithms and data structures, such as depth-first search (DFS), breadth-first search (BFS), minimum spanning tree algorithms (e.g., Kruskal's and Prim's), and various tree data structures like binary search trees or AVL trees.
4. Back Edge - A back edge is an edge that connects a vertex to an ancestor in the depth-first search tree. if `(v, u)` is an edge a back edge is `(u,v)`
5. Forward Edge: A forward edge is an edge that connects a vertex to a descendant in the depth-first search tree.
6. Cross edge: A cross edge connects  two vertices that are not in a parent-child relationship in a DFS.
- More formally, given a DFS traversal of a graph G starting from a particular source vertex, a cross edge is an edge (u, v) in G where u and v are vertices in G, and at the time when the edge is traversed during the DFS, neither u nor v is a descendant of the other in the DFS tree.
- Cross edges can be useful in graph algorithms to identify cycles or other interesting structures in a graph. For example, if a cross edge is encountered during a DFS traversal of a graph, it indicates the presence of a cycle in the graph
1. Directed Edge: An edge with a direction or arrow, representing a one-way relationship or interaction between the vertices.
2.  Undirected Edge: An edge without a direction, representing a two-way relationship or interaction between the vertices.
3.  Weighted Edge: An edge with a numerical value assigned to it, representing a cost or distance associated with the relationship between the vertices.
4.  Degree of a Vertex: The number of edges that are connected to a particular vertex.
5.  Path: A sequence of edges that connects a sequence of vertices in the graph.
6.  Cycle: A closed path in the graph, where the first and last vertices in the path are the same.
7.  Connected Graph: A graph in which there is a path between every pair of vertices.
8.  Connected Component: A subgraph of a graph in which every vertex is connected to at least one other vertex.
9.  Directed Acyclic Graph (DAG): A directed graph with no cycles.
10.  Spanning Tree: A subgraph of a graph that is a tree (a connected acyclic graph) and contains all the vertices of the original graph.

# Applications

- Find any path from a source to all vertices
- Find the lexicographical first path in the graph from source u to all vertices
- Check if a vertex in a tree is an ancestor of some other vertex:
- At the beginning and end of each search call we remember the entry and exit "time" of each vertex, Now you can find the answer for any pair of vertices $(i,j)$ in $O(1)$ time. Vertex `i` is an ancestor of `j` if and only if $entry[i] \lt entry[j]$ and $exit[i] \gt exit[j]$
- Find the LCA of two vertices
- Topological Sorting
- Run a series of DFS so as to visit each vertex exactly once in $O(n + m)$ time. The required topological ordering will be the vertices sorted in descending order of exit time
- Check if graph has cycles (is or isnt acyclic)
- FInd Strongly Connected Components in a directed graph
- First do a topological sorting of the graph. Then transpose the graph and run anohter series of DFS in the order defined by the topological sort. For each DFS save the component created by it as a strongly connected component.
- Find bridges in an undirected graph
- First convert the given graph into a directed graph by running a series of DFS and making each edge directed as we traverse. Second, find the strongly connected components in the directed graph. Bridges are the edges whose ends belong to different strongly connected components

# Implementation

``` java
List<List<Integer>> adj; // graph represented as an adjacency list
int n; // number of vertices

List<Boolean> visited;

void dfs(int v) {
visited.set(v, true);
for (int u : adj.get(v)) {
if (!visited.get(u))
dfs(u);
}
}

//calculating time

List<List<Integer>> adj; // graph represented as an adjacency list
int n; // number of vertices

List<Integer> color;

List<Integer> time_in, time_out;
int dfs_timer = 0;

void dfs(int v) {
time_in.set(v, dfs_timer++);
color.set(v, 1);
for (int u : adj.get(v)) {
if (color.get(u) == 0) {
dfs(u);
}
}
color.set(v, 2);
time_out.set(v, dfs_timer++);
}

```


``` java
private void dfs(int v){
visited[v] = true;
preOrder.offer(v);

for(int neighbor : graph.get(v)){
if(!visited[v]) dfs(v);
}
postOrder.offer(v);
//Reverse Post Order is a Top Sort
reversePostOrder.(v);
}
```

# Connected Components
Given an undirected graph $G$ with $n$  nodes and $m$ edges. We are required to find in it all the connected components, i.e, several groups of vertices such that within a group each vertex can be reached from another and no path exists between different groups.

## An algorithm for solving the problem

-   To solve the problem, we can use Depth First Search or Breadth First Search.
-   In fact, we will be doing a series of rounds of DFS: The first round will start from first node and all the nodes in the first connected component will be traversed (found). Then we find the first unvisited node of the remaining nodes, and run Depth First Search on it, thus finding a second connected component. And so on, until all the nodes are visited.
-   The total asymptotic running time of this algorithm is $O(n + m)$: In fact, this algorithm will not run on the same vertex twice, which means that each edge will be seen exactly two times (at one end and at the other end).


DFS Version to count connected components

``` java
class Solution {
List<List<Integer>> adj = new ArrayList<>();
Set<Integer> visited = new HashSet<>();
public int countComponents(int n, int[][] edges) {
int count = 0;

for(int i = 0; i < n; i++){
adj.add(new ArrayList<>());
}

for(int[] e : edges){
adj.get(e[0]).add(e[1]);
adj.get(e[1]).add(e[0]);
}

for(int i = 0; i < n; i++){
if(!visited.contains(i)){
count++;
dfs(i);
}

}
return count;
}

private void dfs(int v){
visited.add(v);

for(int neighbor : adj.get(v)){
if(!visited.contains(neighbor)){
dfs(neighbor);
}
}
}
}
```

Alternatively we can use Union find for optimal results

# Cycle Check
Cycle in a directed graph
1.	Use a backtracking algorithm
2.	Create a visited array to track if a node has been seen and processed.
3.	Processing array to check if a node is on the recursion stack and not provessed
4.	Intialize the graph according to the parameters
5.	Start Dfs from first available node
-CycleCheck(node)
b.	Processing[node] = true, visited[node] = true;
c.	Go through the edge list of the current vertex
i.	if cycle has been found return (short circuit)
ii.	if processing[node] is true a cycle has been found, update global cycle flag
iii.	if visited[node] is unseen continue DFS
6.	return if cycle has been found


``` java
public class CycleCheck {
boolean[] visited, boolean[] processing;
boolean noCycle = true;
List<List<Integer>> graph = new ArrayList<>();

public boolean canFinish(int n, int[][] edges) {
visited = new boolean[n];
processing = new boolean[n];
//initialize
for (int i = 0; i < n; i++) {
graph.add(new ArrayList<>());
}
for (int[] edge : edges) {
graph.get(edge[0]).add(edge[1]);
}

for (int i = 0; i < n; i++) {
if (!noCycle) break;
if (!visited[i]) cycleCheck(i);

}
return noCycle;
}
private void cycleCheck(int v) {
processing[v] = true;
visited[v] = true;

for (int next : graph.get(v)) {
if (!noCycle) return;
if (processing[next]) {
noCycle = false;
}
if (!visited[next]) cycleCheck(next);
}
processing[v] = false;
}
}
```
Variation: All Paths Lead to destination:

``` java
public boolean allPathsCheck(int source, int destination){
if(onStack[source]) return false;
//When we reach the destination there must be no outgoing edge
if(graph.get(source).isEmpty()) return source == destination;
onStack[source] = true;
for(int neighbors : graph.get(source)){
if(!allPathsCheck(neighbors,destination)) return false;
}
onStack[source] = false;
return true;
}
```

# Is Graph Bipartite
Is Graph Bipartitie?
1.	A simple DFS search
2.	Mark source node color/Boolean value
3.	Run a dfs search from all unvisited nodes
a.	For all children
b.	If they aren’t visited mark them a different color and continue DFS
c.	Else if the colors are equal return false or have flag that says it’s uncolorable
``` java
boolean[] visited;
boolean[] color;
boolean two = true;
int[][] g;

public boolean isBipartite(int[][] graph) {
visited = new boolean[graph.length];
color = new boolean[graph.length];
g = graph;

for (int i = 0; i < graph.length; i++) {
if (!visited[i]) colorCheck(i);
}
return two;
}

private void colorCheck(int v) {
visited[v] = true;

for (int adj : g[v]) {
if (!visited[adj]) {
color[adj] = !color[v];
colorCheck(adj);
} else if (color[adj] == color[v]) two = false;
}
}
```

# Topological Sort



# Finding Bridges in a Graph in O(N + M)


# Eulerian Circuit

Eulerian trail (or **Eulerian path**) is a trail in a finite graph that visits every edge exactly once (allowing for revisiting vertices).  Similarly a Eulerian circuit or **Eulerian cycle** is an Eulerian trail that starts and ends on the same vertex

To summarize, the main idea to find the Eulerian path consists of two steps:

-   Step 1). Starting from any vertex, we keep following the unused edges until we get **stuck** at certain vertex where we have no more unvisited outgoing edges.
-   Step 2). We then backtrack to the nearest neighbor vertex in the current path that has unused edges and we **repeat** the process until all the edges have been used.

The first vertex that we got stuck at would be the **end point** of our **_Eulerian path_**. So if we follow all the stuck _points_ backwards, we could reconstruct the Eulerian path at the end.

1.     Create graph representation and edges
2.     If needed sort lists to find smallest/largest paths
3.     Do a post order depths first search.
4.     When getting  neighbors remove from list instead of using a visited, since we may need to traverse a node multiple times

``` java
public class EulerianPath {
Map<String, ArrayList<String>> map = new HashMap<>();
LinkedList<String> result = new LinkedList<>();

public List<String> findItinerary(List<List<String>> edges) {
for (List<String> edge : edges) {
String k = edge.get(0);
ArrayList<String> v = map.getOrDefault(k, new ArrayList<String>());
v.add(edge.get(1));
this.map.put(k, v);
}

this.map.forEach((key, value) -> Collections.sort(value));
path("JFK");
return this.result;
}

public void path(String start) {
if (this.map.containsKey(start)) {
List<String> neighbors = this.map.get(start);
while (!neighbors.isEmpty()) {
String neighbor = neighbors.remove(0);
path(neighbor);
}
}
this.result.addFirst(start);
}
}
