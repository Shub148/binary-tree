# Sum of Nodes in a Binary Tree (Java)

## Problem Statement

Given the root of a binary tree, find the sum of all node values present in the tree.

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
28
```

### Explanation

```text
1 + 2 + 3 + 4 + 5 + 6 + 7 = 28
```

---

## Approach

This problem can be solved using **Recursion (Depth First Search)**.

### Steps

1. If the current node is `null`, return `0`.
2. Recursively calculate the sum of the left subtree.
3. Recursively calculate the sum of the right subtree.
4. Add:

   * Left subtree sum
   * Right subtree sum
   * Current node value

### Formula

```java
sum(root) = sum(root.left) + sum(root.right) + root.data
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

    public static int sum(Node root) {
        if (root == null) {
            return 0;
        }

        int leftSum = sum(root.left);
        int rightSum = sum(root.right);

        return leftSum + rightSum + root.data;
    }

    public static void main(String args[]) {
        Node root = new Node(1);

        root.left = new Node(2);
        root.right = new Node(3);

        root.left.left = new Node(4);
        root.left.right = new Node(5);

        root.right.left = new Node(6);
        root.right.right = new Node(7);

        System.out.println(sum(root));
    }
}
```

---

## Dry Run

### Leaf Nodes

```text
sum(4) = 4
sum(5) = 5
sum(6) = 6
sum(7) = 7
```

### Internal Nodes

For Node 2:

```text
sum(2) = 4 + 5 + 2
       = 11
```

For Node 3:

```text
sum(3) = 6 + 7 + 3
       = 16
```

### Root Node

```text
sum(1) = 11 + 16 + 1
       = 28
```

### Final Answer

```text
Sum = 28
```

---

## Recursive Tree Visualization

```text
sum(1)
│
├── sum(2)
│   ├── sum(4) = 4
│   └── sum(5) = 5
│
└── sum(3)
    ├── sum(6) = 6
    └── sum(7) = 7
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

Balanced Tree:

```text
O(log n)
```

Skewed Tree:

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

### Difference Between Count, Sum, and Height

| Operation   | Formula                            |
| ----------- | ---------------------------------- |
| Count Nodes | `leftCount + rightCount + 1`       |
| Sum Nodes   | `leftSum + rightSum + root.data`   |
| Height      | `max(leftHeight, rightHeight) + 1` |

### Example

For the tree:

```text
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

```text
Count = 7
Sum = 28
Height = 3
```

---

## Output

```text
28
```

---

## Learning Outcomes

After solving this problem, you will understand:

* Recursive Tree Traversal
* Divide and Conquer Strategy
* Binary Tree Fundamentals
* DFS (Depth First Search)
* Time and Space Complexity Analysis

This is a commonly asked Binary Tree interview question in coding interviews and competitive programming.
