# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE:17-09-2026
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Start the program.

2. Read n, the number of nodes, and e, the number of edges. Build an undirected graph using an adjacency list by adding both u → v and v → u for each edge.

3. For shortestPath():

Perform BFS starting from the given start node.
Mark the start node as visited and initialize its distance as 0.
For each unvisited adjacent node, mark it visited and update its distance.
Return the distance when the target node is reached.
If the target node is unreachable, return -1.
For reachableAttractions():

4. Perform DFS starting from the given start node.
5. Mark each visited node as reachable.
6. Continue until all reachable nodes have been visited.
7. Count the number of nodes marked as visited to determine the total number of reachable attractions.

8. Display the shortest path distance and the total number of reachable attractions from the start node.

9. End the program.  

## Program:
```
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: JAI HARISH R
RegisterNumber:  212224040124
*/
```

```java

import java.util.*;

public class TouristNavigation {
    
    public static int shortestPath(List<List<Integer>> graph, int start, int target, int n) {
      //Type your code
      boolean[] visited = new boolean[n];
        int[] distance = new int[n];
        Arrays.fill(distance, -1); // -1 means unreachable

        Queue<Integer> queue = new LinkedList<>();
        queue.offer(start);
        visited[start] = true;
        distance[start] = 0;

        while (!queue.isEmpty()) {
            int current = queue.poll();

            // If we reached the target
            if (current == target) {
                return distance[current];
            }

            for (int neighbor : graph.get(current)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    distance[neighbor] = distance[current] + 1;
                    queue.offer(neighbor);
                }
            }
        }

        // Target unreachable
        return -1;
    }

    public static void reachableAttractions(List<List<Integer>> graph, boolean[] visited, int node) {
        //Type your code
        visited[node] = true;
        for (int neighbor : graph.get(node)) {
            if (!visited[neighbor]) {
                reachableAttractions(graph, visited, neighbor);
            }
        }
    }

    public static int countReachable(boolean[] visited) {
        //Type your code
        int count = 0;
        for (boolean v : visited) {
            if (v) count++;
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), e = sc.nextInt();
        List<List<Integer>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        for (int i = 0; i < e; i++) {
            int u = sc.nextInt(), v = sc.nextInt();
            graph.get(u).add(v);
            graph.get(v).add(u);
        }

        int start = sc.nextInt();
        int target = sc.nextInt();

        int shortest = shortestPath(graph, start, target, n);
        boolean[] visited = new boolean[n];
        reachableAttractions(graph, visited, start);
        int reachable = countReachable(visited);

        System.out.println("Shortest path from start to target: " + shortest);
        System.out.println("Total reachable attractions from start: " + reachable);
    }
}


```

## Output:

<img width="965" height="308" alt="image" src="https://github.com/user-attachments/assets/3c57358d-3352-479a-b1f0-8f3e1783003b" />


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
