# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE:17-09-2026
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start the program.

2. Read n and insert each of the n book IDs into a Binary Search Tree using the insert() method.

3. In the insert() method:

4. If the tree is empty, create a new node.
Otherwise, recursively insert the key into the left or right subtree based on comparison.
5. Read q, the number of search queries.

6. For each query, use the search() method:

7. If the current node is null, return false.
8. If the node's value matches the key, return true.
9. Otherwise, recursively search the left or right subtree based on comparison.
10. Print "Found" if the key exists in the BST; otherwise, print "Not Found".

11. Stop the program. 

## Program:
```
/*
Program to constructs a Binary Search Tree (BST) using given Book IDs 
Developed by: JAI HARISH R
RegisterNumber:  212224040124
*/
```

```java

import java.util.*;

public class BookIDSearch {
    

    public static Node insert(Node root, int key) {
        //Type your Code
        if (root == null) 
        return new Node(key);
        if (key < root.data) 
        root.left = insert(root.left, key);
        else 
        root.right = insert(root.right, key);
        return root;
    }

    public static boolean search(Node root, int key) {
        //Type your Code
        if (root == null) 
        return false;
        if (root.data == key) 
        return true;
        return (key < root.data) ? search(root.left, key) : search(root.right, key);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Node root = null;
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }
        int q = sc.nextInt();
        while (q-- > 0) {
            int key = sc.nextInt();
            System.out.println(search(root, key) ? "Found" : "Not Found");
        }
    }
}
class Node {
        int data;
        Node left, right;
        Node(int data) {
            this.data = data;
        }
    }


```

## Output:

<img width="612" height="252" alt="image" src="https://github.com/user-attachments/assets/d81cef72-32c5-491e-b88d-b64e9e63182e" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
