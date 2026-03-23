# Experiment 18d: Prim's Minimum Spanning Tree (MST)

## Aim
To write a Python program for Prim's Minimum Spanning Tree (MST) algorithm.

---

## Algorithm

1. **Initialize Key Array**:
   - Initialize a `key` array to represent the minimum weight edge for each vertex, setting all values to infinity except for the first vertex, which is set to 0.

2. **Select the Minimum Key Vertex**:
   - Use the `minKey()` function to find the vertex with the smallest key value that is not yet included in the MST.

3. **Update Key Values**:
   - For each adjacent vertex of the selected vertex, if the edge weight is smaller than the current key value and the vertex is not in the MST, update the key value and parent of the vertex.

4. **Repeat**:
   - Repeat steps 2 and 3 for all vertices until all vertices are included in the MST.

5. **Print the MST**:
   - Finally, print the Minimum Spanning Tree using the parent array which holds the parent vertex for each vertex in the MST.

---

## Program

```
import sys # Library for INT_MAX
class Graph():
	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]
	def printMST(self, parent):
		print ("Edge   Weight")
		for i in range(1, self.V):
			print (parent[i], "-", i, "  ",self.graph[i][parent[i]])
	def minKey(self, key, mstSet):
		min = sys.maxsize
		for v in range(self.V):
			if key[v] < min and mstSet[v] == False:
				min = key[v]
				min_index = v
		return min_index
	def primMST(self):
		key = [sys.maxsize] * self.V
		parent = [None] * self.V
		key[0] = 0
		mstSet = [False] * self.V
		parent[0] = -1
		for cout in range(self.V):
			u=self.minKey(key,mstSet)
			mstSet[u]=True
			for v in range(self.V):
			    if self.graph[u][v]>0 and mstSet[v]==False and key[v]>self.graph[u][v]:
			        key[v]=self.graph[u][v]
			        parent[v]=u
		self.printMST(parent)
g = Graph(5)
g.graph = [ [0, 2, 0, 6, 0],
			[2, 0, 3, 8, 5],
			[0, 3, 0, 0, 7],
			[6, 8, 0, 0, 9],
			[0, 5, 7, 9, 0]]

g.primMST();
```

## OUTPUT
<img width="1185" height="285" alt="image" src="https://github.com/user-attachments/assets/1b8062f5-dd0e-45fe-8aff-b66d8901eba8" />

## RESULT
Therefore, the output is the example to write a Python program for Prim's Minimum Spanning Tree (MST) algorithm.
