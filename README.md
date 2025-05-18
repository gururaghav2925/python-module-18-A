# Prim's Minimum Spanning Tree (MST) Algorithm using Python

# Aim
To implement Prim's algorithm in Python to find the Minimum Spanning Tree (MST) of a connected, weighted, undirected graph.

# Procedure
1. Begin by understanding the structure of a weighted undirected graph.
2. Represent the graph using a suitable data structure (e.g., adjacency list or matrix).
3. Select a starting vertex and initialize the MST set and a priority queue for selecting minimum weight edges.
4. At each step, pick the edge with the smallest weight that connects a new vertex to the MST.
5. Add the selected edge and vertex to the MST.
6. Repeat the process until all vertices are included in the MST.
7. Calculate and display the edges included in the MST along with the total minimum cost.
# Program
```python
import sys

class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0 for column in range(vertices)] for row in range(vertices)]

    def printMST(self, parent):
        print("Edge   Weight")
        for i in range(1, self.V):
            print(f"{parent[i]} - {i}    {self.graph[i][parent[i]]}")

    def minKey(self, key, mstSet):
        min_val = sys.maxsize
        min_index = -1
        for v in range(self.V):
            if key[v] < min_val and not mstSet[v]:
                min_val = key[v]
                min_index = v
        return min_index

    def primMST(self):
        key = [sys.maxsize] * self.V  
        parent = [None] * self.V      
        key[0] = 0                    
        mstSet = [False] * self.V    

        parent[0] = -1  

        for _ in range(self.V):
            u = self.minKey(key, mstSet)
            mstSet[u] = True

            for v in range(self.V):
                if self.graph[u][v] > 0 and not mstSet[v] and key[v] > self.graph[u][v]:
                    key[v] = self.graph[u][v]
                    parent[v] = u

        self.printMST(parent)

# Example usage:
g = Graph(5)
g.graph = [
    [0, 2, 0, 6, 0],
    [2, 0, 3, 8, 5],
    [0, 3, 0, 0, 7],
    [6, 8, 0, 0, 9],
    [0, 5, 7, 9, 0]
]

g.primMST()

```

# Output

![image](https://github.com/user-attachments/assets/1d1bd87c-f7bb-426a-92f8-104a135717c2)

# Result
Prim's algorithm is successfully implemented using Python. The program generates the Minimum Spanning Tree by selecting edges with the least weights while connecting all vertices without forming cycles. The final MST and its total cost are displayed.
