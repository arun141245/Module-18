# Experiment 18c: Kruskal's Algorithm

## Aim
To write a Python program for Kruskal's algorithm to find the Minimum Spanning Tree (MST) of a given connected, undirected, and weighted graph.

---

## Algorithm

1. **Sort all edges**:
   - Sort all the edges in non-decreasing order of their weights.

2. **Initialize parent and rank arrays**:
   - Initialize the `parent` array to keep track of the set to which each vertex belongs.
   - Initialize the `rank` array to manage the union of sets efficiently.

3. **Iterate over sorted edges**:
   - Pick the smallest edge and check if it forms a cycle with the MST formed so far by checking if the vertices are in the same set.
   
4. **Check and add the edge**:
   - If it doesn't form a cycle, include this edge in the MST and perform a union of the two sets.

5. **Repeat until MST contains V-1 edges**:
   - Continue adding edges to the MST until it contains `V-1` edges, where `V` is the number of vertices.

6. **Print the MST**:
   - Finally, print the edges in the MST along with the minimum cost.

---

## Program

```
from collections import defaultdict
class Graph:
	def __init__(self, vertices):
		self.V = vertices
		self.graph = []
	def addEdge(self, u, v, w):
		self.graph.append([u, v, w])
	def find(self, parent, i):
		if parent[i] == i:
			return i
		return self.find(parent, parent[i])
	def union(self, parent, rank, x, y):
		xroot = self.find(parent, x)
		yroot = self.find(parent, y)
		if rank[xroot] < rank[yroot]:
			parent[xroot] = yroot
		elif rank[xroot] > rank[yroot]:
			parent[yroot] = xroot
		else:
			parent[yroot] = xroot
			rank[xroot] += 1
	def KruskalMST(self):
		result = []
		i = 0
		e = 0
		self.graph = sorted(self.graph,
							key=lambda item: item[2])
		parent = []
		rank = []
		for node in range(self.V):
		    parent.append(node)
		    rank.append(0)
		while e<self.V-1:
			u,v,w=self.graph[i]
			i=i+1
			x=self.find(parent,u)
			y=self.find(parent,v)
			if x!=y:
			    e=e+1
			    result.append([u,v,w])
			    self.union(parent,rank,x,y)
		minimumCost=0
		print("Edges in the constructed MST")
		for u,v,weight in result:
		    minimumCost+=weight
		    print("%d -- %d == %d" % (u,v,weight))
		print("Minimum Spanning Tree",minimumCost)
g = Graph(4)
g.addEdge(0, 1, 10)
g.addEdge(0, 2, 6)
g.addEdge(0, 3, 5)
g.addEdge(1, 3, 15)
g.addEdge(2, 3, 4)
g.KruskalMST()
```

## OUTPUT
<img width="1185" height="285" alt="image" src="https://github.com/user-attachments/assets/54248e91-2ba6-4531-b02d-323107f2f46a" />

## RESULT
Therefore, the output is the example to write a Python program for Kruskal's algorithm to find the Minimum Spanning Tree (MST) of a given connected, undirected, and weighted graph.
