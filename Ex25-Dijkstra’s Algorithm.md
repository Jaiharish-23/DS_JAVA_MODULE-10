# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE:17-09-2026
## AIM:
To design and implement a java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Start the program.
2. Read n, the number of nodes, and m, the number of weighted edges. Build an undirected graph using an adjacency list where each edge stores the neighboring node and travel time.
3. Read the source node and the set of charging-station nodes.
4. Initialize a distance array with infinity and set the distance of the source node to 0.
5. Use Dijkstra’s algorithm:
Push (source, 0) into a min-heap.
Repeatedly extract the node with the smallest travel time.
If the extracted node is a charging station, return its travel time.
Relax its neighboring edges and update their distances if a shorter path is found.
If no charging station is reachable, return -1.
6. Display the minimum travel time to the nearest reachable charging station.
7. End the program.  

## Program:
```
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: JAI HARISH R
RegisterNumber:  212224040124
*/
```

```java

import java.util.*;

public class EVChargingNavigation {

    static class Pair {
        int node, time;
        Pair(int node, int time) {
            this.node = node;
            this.time = time;
        }
    }

    static int findNearestChargingStation(int n, List<List<Pair>> graph, int source, Set<Integer> stations) {
        //Type your code
        int[] dist = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[source] = 0;

        // Min-heap for (time, node)
        PriorityQueue<Pair> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a.time));
        pq.offer(new Pair(source, 0));

        while (!pq.isEmpty()) {
            Pair current = pq.poll();
            int node = current.node;
            int time = current.time;

            // Skip outdated entries
            if (time > dist[node]) continue;

            // If current node is a charging station, return its distance
            if (stations.contains(node)) {
                return time;
            }

            // Explore neighbors
            for (Pair neighbor : graph.get(node)) {
                int newTime = time + neighbor.time;
                if (newTime < dist[neighbor.node]) {
                    dist[neighbor.node] = newTime;
                    pq.offer(new Pair(neighbor.node, newTime));
                }
            }
        }

        // If no charging station is reachable
        return -1;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt(), m = sc.nextInt();
        List<List<Pair>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        for (int i = 0; i < m; i++) {
            int u = sc.nextInt(), v = sc.nextInt(), w = sc.nextInt();
            graph.get(u).add(new Pair(v, w));
            graph.get(v).add(new Pair(u, w)); // Undirected
        }

        int source = sc.nextInt();
        int k = sc.nextInt();
        Set<Integer> stations = new HashSet<>();
        for (int i = 0; i < k; i++) stations.add(sc.nextInt());

        System.out.println(findNearestChargingStation(n, graph, source, stations));
    }
}


```

## Output:

<img width="640" height="367" alt="image" src="https://github.com/user-attachments/assets/05f95fc5-0d4c-40b5-bcae-71824c0eb511" />

## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
