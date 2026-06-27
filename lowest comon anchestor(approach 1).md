# 🌳 Lowest Common Ancestor (LCA) in Binary Tree - Approach 1 (Using Paths)

## 📌 Problem Statement

Given a binary tree and two nodes `n1` and `n2`, find their **Lowest Common Ancestor (LCA)**.

The **Lowest Common Ancestor (LCA)** of two nodes is the **lowest node in the tree that has both nodes as descendants** (where a node can be a descendant of itself).

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
n1 = 4
n2 = 5
```

### Output

```text
2
```

---

# Approach 1 : Using Root-to-Node Paths

The idea is simple.

1. Find the path from the **root to node n1**.
2. Find the path from the **root to node n2**.
3. Compare both paths.
4. The last common node in both paths is the **Lowest Common Ancestor (LCA).**

---

# Algorithm

### Step 1 : Find Path

* Start from the root.
* Store every visited node in an ArrayList.
* If the target node is found, return `true`.
* Otherwise backtrack by removing the current node from the path.

### Step 2 : Compare Paths

Suppose

```text
Path to 4 : 1 → 2 → 4

Path to 5 : 1 → 2 → 5
```

Compare both paths from the beginning.

```text
1 == 1 ✔
2 == 2 ✔
4 != 5 ❌
```

The last common node is **2**, which is the LCA.

---

# Dry Run

For

```text
n1 = 4
n2 = 5
```

### Path to 4

```text
1 → 2 → 4
```

### Path to 5

```text
1 → 2 → 5
```

### Comparison

| Path 1 | Path 2 | Same? |
| ------ | ------ | ----- |
| 1      | 1      | ✅     |
| 2      | 2      | ✅     |
| 4      | 5      | ❌     |

Last common node = **2**

Output

```text
2
```

---

# Time Complexity

### getPath()

Each call may visit every node once.

```text
O(n)
```

It is called twice.

```text
O(n) + O(n) = O(n)
```

Comparing the two paths

```text
O(h)
```

where **h** is the height of the tree.

Overall

```text
O(n)
```

---

# Space Complexity

Two ArrayLists store the root-to-node paths.

```text
O(h)
```

Recursive call stack

```text
O(h)
```

Overall

```text
O(h)
```

Worst Case (Skewed Tree)

```text
O(n)
```

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

    public static boolean getPath(Node root, int n, ArrayList<Node> path) {

        if (root == null) {
            return false;
        }

        path.add(root);

        if (root.data == n) {
            return true;
        }

        boolean foundLeft = getPath(root.left, n, path);
        boolean foundRight = getPath(root.right, n, path);

        if (foundLeft || foundRight) {
            return true;
        }

        path.remove(path.size() - 1);
        return false;
    }

    public static Node lca(Node root, int n1, int n2) {

        ArrayList<Node> path1 = new ArrayList<>();
        ArrayList<Node> path2 = new ArrayList<>();

        getPath(root, n1, path1);
        getPath(root, n2, path2);

        int i = 0;

        for (; i < path1.size() && i < path2.size(); i++) {

            if (path1.get(i) != path2.get(i)) {
                break;
            }
        }

        Node lca = path1.get(i - 1);

        return lca;
    }

    public static void main(String[] args) {

        Node root = new Node(1);

        root.left = new Node(2);
        root.right = new Node(3);

        root.left.left = new Node(4);
        root.left.right = new Node(5);

        root.right.left = new Node(6);
        root.right.right = new Node(7);

        int n1 = 4;
        int n2 = 5;

        System.out.println(lca(root, n1, n2).data);
    }
}
```

---

# Output

```text
2
```

---

# Key Points

* Uses **two root-to-node paths** to find the LCA.
* First finds the path to `n1`, then the path to `n2`.
* Compares both paths to identify the last common node.
* Easy to understand and implement.
* Time Complexity: **O(n)**
* Space Complexity: **O(h)** (or **O(n)** in the worst case).
* This is commonly referred to as **Approach 1**. A more optimized **Approach 2** solves the problem without storing paths.
