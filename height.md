# Height of a Binary Tree in Java

## Problem Statement

Given the root of a binary tree, find the height of the tree.

The height of a binary tree is the number of nodes along the longest path from the root node to the deepest leaf node.

### Example Tree

```text
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

### Output

```text
3
```

The longest path is:

```text
1 → 2 → 4
```

or

```text
1 → 2 → 5
```

or

```text
1 → 3 → 6
```

or

```text
1 → 3 → 7
```

Each path contains 3 nodes, so the height is 3.

---

## Approach

This problem can be solved using **Recursion (Depth First Search)**.

### Steps

1. If the current node is `null`, return `0`.
2. Recursively calculate the height of the left subtree.
3. Recursively calculate the height of the right subtree.
4. Return the maximum of left height and right height plus `1`.

### Formula

```java
height(root) = max(height(root.left), height(root.right)) + 1
```

---

## Java Implementation

```java
import java.util.*;

public class classroom {
    static class Node {
        int data;
        Node left, right;

        public Node(int data) {
            this.data = data;
            this.left = null;
            this.right = null;
        }
    }

    public static int height(Node root) {
        if (root == null) {
            return 0;
        }

        int lh = height(root.left);
        int rh = height(root.right);

        return Math.max(lh, rh) + 1;
    }

    public static void main(String args[]) {
        Node root = new Node(1);

        root.left = new Node(2);
        root.right = new Node(3);

        root.left.left = new Node(4);
        root.left.right = new Node(5);

        root.right.left = new Node(6);
        root.right.right = new Node(7);

        System.out.println(height(root));
    }
}
```

---

## Dry Run

For Node 4:

```text
height(4) = 1
```

For Node 5:

```text
height(5) = 1
```

For Node 2:

```text
height(2) = max(1,1) + 1 = 2
```

For Node 3:

```text
height(3) = max(1,1) + 1 = 2
```

For Root Node 1:

```text
height(1) = max(2,2) + 1 = 3
```

### Final Answer

```text
Height = 3
```

---

## Complexity Analysis

### Time Complexity

```text
O(n)
```

Every node is visited exactly once.

### Space Complexity

```text
O(h)
```

Where `h` is the height of the tree due to recursion stack space.

Worst Case:

```text
O(n)
```

For a skewed tree.

Balanced Tree:

```text
O(log n)
```

---

## Key Concepts

* Binary Tree
* Recursion
* Depth First Search (DFS)
* Tree Traversal
* Divide and Conquer

---

### Interview Tip

A very common interview question is:

> What is the difference between Height and Depth?

* Height = Longest path from a node to a leaf.
* Depth = Distance from the root to a node.

For the root node:

```text
Depth = 0
Height = Height of entire tree
```
