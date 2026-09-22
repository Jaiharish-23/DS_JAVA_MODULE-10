# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE:17-09-2026
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Start the program.

2. Read n and store the n input values in an array.

3. Build a binary tree in level order by creating the root and assigning left and right children sequentially using a queue.

4. Check whether the root has a left child:

5. If there is no left child, print 0.
Otherwise, continue to the next step.
6. Recursively count the nodes in the left subtree using the countNodes() method.

7. The countNodes() method returns 1 plus the number of nodes in the left and right subtrees.

8. Print the total number of nodes in the left subtree.

9. Stop the program.   

## Program:
```
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: JAI HARISH R
RegisterNumber:  212224040124
*/
```

```java

import java.util.*;

class Node {
    int data;
    Node left, right;
    Node(int data) {
        this.data = data;
        this.left = this.right = null;
    }
}

public class Main {

    // Build binary tree in level-order fashion
    static Node buildTree(int[] arr) {
        if (arr.length == 0) return null;
        Node root = new Node(arr[0]);
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        int i = 1;

        while (!q.isEmpty() && i < arr.length) {
            Node current = q.poll();
            if (i < arr.length) {
                current.left = new Node(arr[i++]);
                q.add(current.left);
            }
            if (i < arr.length) {
                current.right = new Node(arr[i++]);
                q.add(current.right);
            }
        }

        return root;
    }

    static int countNodes(Node root) {
        if (root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = sc.nextInt();
        Node root = buildTree(arr);

        if (root.left == null) {
            System.out.println(0);
        } else {
            System.out.println(countNodes(root.left));
        }
    }
}


```

## Output:

<img width="655" height="182" alt="image" src="https://github.com/user-attachments/assets/4e020dd1-64a3-422b-a289-922ad267da2b" />


## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
