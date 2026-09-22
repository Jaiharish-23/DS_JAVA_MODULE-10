# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE:17-09-2026
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Start the program.

2. Read n, the number of nodes, and e, the number of edges. Create an adjacency list with n empty lists.

3. For each edge, read its endpoints u and v, and add both u → v and v → u to the graph using the addEdge() method.

4. Read the source node src for the BFS traversal.

5. In the bfs() method:

6. Mark the source node as visited.

7. Add the source node to a queue.

8. While the queue is not empty:

9. Remove a node from the queue and display it.
10. Visit all its unvisited adjacent nodes.
11. Mark each unvisited neighbor as visited and add it to the queue.
12. Stop the program. 

## Program:
```
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: JAI HARISH R
RegisterNumber:  212224040124
*/
```

```java

import java.util.*;

public class EmergencyRouteBFS {
    public static void addEdge(List<List<Integer>> g, int u, int v) {
        //Type your Code
        g.get(u).add(v);
        g.get(v).add(u);
    }

    public static void bfs(List<List<Integer>> g, int src, boolean[] visited) {
        //Type your Code
        Queue<Integer> q = new LinkedList<>();
        q.offer(src);
        visited[src] = true;
        while (!q.isEmpty()) {
            int curr = q.poll();
            System.out.print(curr + " ");
            for (int neighbor : g.get(curr)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.offer(neighbor);
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), e = sc.nextInt();
        List<List<Integer>> g = new ArrayList<>();
        for (int i = 0; i < n; i++) g.add(new ArrayList<>());
        for (int i = 0; i < e; i++) addEdge(g, sc.nextInt(), sc.nextInt());
        int src = sc.nextInt();
        bfs(g, src, new boolean[n]);
    }
}


```

## Output:

<img width="555" height="283" alt="image" src="https://github.com/user-attachments/assets/5c4c0563-2b02-44ac-8d11-d8919db0f5cb" />

## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
