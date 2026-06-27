# 🌳 Kth Level of Binary Tree (Java)

## 📌 Problem Statement

Given a binary tree and an integer **K**, print all the nodes present at the **Kth level** of the tree.

* Root is considered at **Level = 1**
* Print all nodes at the given level from **left to right**.

---

# Example Binary Tree

```text
          1
        /   \
       2     3
      / \   / \
     4   5 6   7
```

### Input

```text
K = 3
```

### Output

```text
4 5 6 7
```

---

# Approach

We use **Recursion (Preorder Traversal)**.

### Steps

1. Start from the root with `level = 1`.
2. If the current node is `null`, return.
3. If `level == k`

   * Print the node.
   * Return.
4. Recursively visit

   * Left Subtree
   * Right Subtree
5. Increase the level by `1` in every recursive call.

---

# Algorithm

```text
kLevel(root, level, k)

If root == null
    return

If level == k
    print(root.data)
    return

Call kLevel(root.left, level + 1, k)

Call kLevel(root.right, level + 1, k)
```

---

# Dry Run

For

```text
K = 3
```

Traversal

```text
Node 1 (Level 1)
│
├── Node 2 (Level 2)
│      ├── Node 4 (Level 3) ✅ Print
│      └── Node 5 (Level 3) ✅ Print
│
└── Node 3 (Level 2)
       ├── Node 6 (Level 3) ✅ Print
       └── Node 7 (Level 3) ✅ Print
```

Output

```text
4 5 6 7
```

---

# Time Complexity

```text
O(n)
```

Every node is visited at most once.

---

# Space Complexity

```text
O(h)
```

Where

* **h** = Height of Binary Tree
* Space is used by the recursive call stack.

Worst Case

```text
O(n)
```

(Skewed Tree)

Balanced Tree

```text
O(log n)
```

---

# Java Code

```java
import java.util.*;

public class file {

    static class Node {
        int data;
        Node right, left;

        public Node(int data) {
            this.data = data;
            this.right = null;
            this.left = null;
        }
    }

    public static void klevel(Node root, int level, int k) {

        if (root == null) {
            return;
        }

        if (level == k) {
            System.out.print(root.data + " ");
            return;
        }

        klevel(root.left, level + 1, k);
        klevel(root.right, level + 1, k);
    }

    public static void main(String[] args) {

        Node root = new Node(1);

        root.left = new Node(2);
        root.right = new Node(3);

        root.left.left = new Node(4);
        root.left.right = new Node(5);

        root.right.left = new Node(6);
        root.right.right = new Node(7);

        int k = 3;

        klevel(root, 1, k);
    }
}
```

---

# Output

```text
4 5 6 7
```

---

## Key Points

* Uses **Depth First Search (DFS)** recursion.
* Root starts from **Level 1**.
* Left subtree is visited before the right subtree.
* Prints all nodes present exactly at the **Kth level**.
* Efficient solution with **O(n)** time complexity.
* No extra data structures (Queue, List, etc.) are required.
