# Count Number of Nodes in a Binary Tree (Java)

## Problem Statement

Given the root of a binary tree, find the total number of nodes present in the tree.

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
7
```

The tree contains 7 nodes:
1, 2, 3, 4, 5, 6, and 7.

---

## Approach

This problem can be solved using **Recursion (Depth First Search)**.

### Steps

1. If the current node is `null`, return `0`.
2. Recursively count nodes in the left subtree.
3. Recursively count nodes in the right subtree.
4. Add:

   * Left subtree count
   * Right subtree count
   * Current node (1)

### Formula

```java
count(root) = count(root.left) + count(root.right) + 1
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

    public static int count(Node root) {
        if (root == null) {
            return 0;
        }

        int leftCount = count(root.left);
        int rightCount = count(root.right);

        return leftCount + rightCount + 1;
    }

    public static void main(String args[]) {
        Node root = new Node(1);

        root.left = new Node(2);
        root.right = new Node(3);

        root.left.left = new Node(4);
        root.left.right = new Node(5);

        root.right.left = new Node(6);
        root.right.right = new Node(7);

        System.out.println(count(root));
    }
}
```

---

## Dry Run

### Leaf Nodes

```text
count(4) = 1
count(5) = 1
count(6) = 1
count(7) = 1
```

### Internal Nodes

```text
count(2) = 1 + 1 + 1 = 3
count(3) = 1 + 1 + 1 = 3
```

### Root Node

```text
count(1) = 3 + 3 + 1 = 7
```

### Final Answer

```text
Total Nodes = 7
```

---

## Recursive Tree Visualization

```text
count(1)
│
├── count(2)
│   ├── count(4) = 1
│   └── count(5) = 1
│
└── count(3)
    ├── count(6) = 1
    └── count(7) = 1
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

Where:

* `h` = Height of the tree

For a balanced tree:

```text
O(log n)
```

For a skewed tree:

```text
O(n)
```

---

## Key Concepts

* Binary Tree
* Recursion
* Depth First Search (DFS)
* Tree Traversal
* Divide and Conquer

---

## Interview Tip

### Difference Between Count and Height

**Count of Nodes**

```text
Total number of nodes in the tree.
```

Example:

```text
1, 2, 3, 4, 5, 6, 7
Count = 7
```

**Height of Tree**

```text
Number of nodes on the longest path from root to leaf.
```

Example:

```text
1 → 2 → 4
Height = 3
```

---

## Output

```text
7
```
