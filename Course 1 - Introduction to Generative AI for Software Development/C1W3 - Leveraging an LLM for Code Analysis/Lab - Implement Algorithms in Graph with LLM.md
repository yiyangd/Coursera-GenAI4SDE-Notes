## 1 - Introduction

Welcome to the first assignment of Course 1 in the Generative AI for Software Development Specialization! In this assignment you will **work alongside an LLM to take on four different graph-based problems** including finding the shortest path through a graph and solving different variations of the classic Travelling Salesman Problem in which you must find the shortest tour through every vertex in the graph. This is a great opportunity to practice using the LLM skills you've been learning! 

**Here's a quick summary of the contents of this notebook:**

- Section 1: Introduction, setup, and the `Graph` class this assignment is based on
- Section 2: The `Graph_Advanced` class that you will edit for your submission
- Section 3: Description of the four exercises you'll implement inside of `Graph_Advanced`
- Section 4: A playground to test solutions
- Section 5: Unit tests of your `Graph_Advanced` class

**Here's a few important points on how this notebook works:**

- **Only `Graph_Advanced` is Graded:** You can add new cells to experiment but these will be ignored by the grader. If you want something graded, include it in the provided cell that contains the `Graph_Advanced` class.
- **Some Cells are Frozen:** Some cells are frozen, e.g. the `Graph` class, to avoid mistakenly editing their code
- **Avoid importing new libraries:** Avoid importing new libraries beyond those you'll find in section 1.1, immediately below. In particular `joblib` or any multiprocessing or parallel computing approach will crash the grader. If you absolutely need additional libraries, import them in the same cell as the `Graph_Advanced` class.
- **Save before submitting:** Do this to ensure you are graded on your most recent work.

**IMPORTANT NOTES ON THE AUTOGRADING SYSTEM**
- The graded cells are tagged, meaning the autograder specifically looks for them when grading. Therefore, **do not delete these cells or add your solution in another cell**, as this will cause the autograder to malfunction. If you accidentally delete a cell or encounter any unusual issues with the autograder, please [refresh your workspace](https://www.coursera.org/learn/introduction-to-generative-ai-for-software-development/item/qEB8o) to obtain a new copy of the assignment and place your solution in the designated solution cells.
- The autograder **does not have access** to the **unittests** library, so **avoid importing it or using any unittest functions within a graded cell**, as this will disrupt the autograder's functionality.
- If you face any challenges or have questions about this assignment, feel free to [join our community](https://www.coursera.org/learn/introduction-to-generative-ai-for-software-development/supplement/hIZen/important-have-questions-issues-or-ideas-join-our-forum) and seek assistance from our mentors!

Happy coding!

### 1.1 - Importing necessary libraries

The code below imports libraries used in this assignment. You should be able to complete this assignment without additional libraries. If you absolutely need additional libraries, import them in the same cell as the `Graph_Advanced` class.

```python
import random
import heapq
import os
import numpy as np
import itertools
```

### 1.2 - Importing unittests

This library includes unit tests to evaluate your solutions. More information on unit testing is in Section 5.

```python
import unittests
```

### 1.3 - The `Graph` Class

The `Graph` class that defines the structure of a graph and the methods that can be performed on them. Take a moment to familiarize yourself with the class's structure and its methods, or better yet, share the code with an LLM and ask it for an explanation!

```python
class Graph:
    def __init__(self, directed=False):
        """
        Initialize the Graph.

        Parameters:
        - directed (bool): Specifies whether the graph is directed. Default is False (undirected).

        Attributes:
        - graph (dict): A dictionary to store vertices and their adjacent vertices (with weights).
        - directed (bool): Indicates whether the graph is directed.
        """
        self.graph = {}
        self.directed = directed
    
    def add_vertex(self, vertex):
        """
        Add a vertex to the graph.

        Parameters:
        - vertex: The vertex to add. It must be hashable.

        Ensures that each vertex is represented in the graph dictionary as a key with an empty dictionary as its value.
        """
        if not isinstance(vertex, (int, str, tuple)):
            raise ValueError("Vertex must be a hashable type.")
        if vertex not in self.graph:
            self.graph[vertex] = {}
    
    def add_edge(self, src, dest, weight):
        """
        Add a weighted edge from src to dest. If the graph is undirected, also add from dest to src.

        Parameters:
        - src: The source vertex.
        - dest: The destination vertex.
        - weight: The weight of the edge.
        
        Prevents adding duplicate edges and ensures both vertices exist.
        """
        if src not in self.graph or dest not in self.graph:
            raise KeyError("Both vertices must exist in the graph.")
        if dest not in self.graph[src]:  # Check to prevent duplicate edges
            self.graph[src][dest] = weight
        if not self.directed and src not in self.graph[dest]:
            self.graph[dest][src] = weight
    
    def remove_edge(self, src, dest):
        """
        Remove an edge from src to dest. If the graph is undirected, also remove from dest to src.

        Parameters:
        - src: The source vertex.
        - dest: The destination vertex.
        """
        if src in self.graph and dest in self.graph[src]:
            del self.graph[src][dest]
        if not self.directed:
            if dest in self.graph and src in self.graph[dest]:
                del self.graph[dest][src]
    
    def remove_vertex(self, vertex):
        """
        Remove a vertex and all edges connected to it.

        Parameters:
        - vertex: The vertex to be removed.
        """
        if vertex in self.graph:
            # Remove any edges from other vertices to this one
            for adj in list(self.graph):
                if vertex in self.graph[adj]:
                    del self.graph[adj][vertex]
            # Remove the vertex entry itself
            del self.graph[vertex]
    
    def get_adjacent_vertices(self, vertex):
        """
        Get a list of vertices adjacent to the specified vertex.

        Parameters:
        - vertex: The vertex whose neighbors are to be retrieved.

        Returns:
        - List of adjacent vertices. Returns an empty list if vertex is not found.
        """
        return list(self.graph.get(vertex, {}).keys())

    def _get_edge_weight(self, src, dest):
        """
        Get the weight of the edge from src to dest.

        Parameters:
        - src: The source vertex.
        - dest: The destination vertex.

        Returns:
        - The weight of the edge. If the edge does not exist, returns infinity.
        """
        return self.graph[src].get(dest, float('inf'))
    
    def __str__(self):
        """
        Provide a string representation of the graph's adjacency list for easy printing and debugging.

        Returns:
        - A string representation of the graph dictionary.
        """
        return str(self.graph)
```
