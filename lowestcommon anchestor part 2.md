# Lowest Common Ancestor (LCA) in Binary Tree - Approach 2 (Optimized Recursive)

## 📌 Problem Statement

Given a Binary Tree and two nodes `n1` and `n2`, find their **Lowest Common Ancestor (LCA)**.

The **Lowest Common Ancestor (LCA)** is the deepest node in the tree that has both `n1` and `n2` as descendants.

---

## 🌳 Example

```
          1
        /   \
       2     3
      / \   / \
     4   5 6   7
```

### Input

```
n1 = 4
n2 = 7
```

### Output

```
1
```

Because node **1** is the lowest node having both **4** and **7** as descendants.

---

# 🚀 Approach 2 (Optimized Recursive Solution)

Unlike **Approach 1**, we do **not store paths** from the root to each node.

Instead, we recursively search for both nodes in the left and right subtrees.

This approach is more efficient and uses less extra memory.

---

# 💡 Algorithm

### Step 1

If the current node is `null`, return `null`.

```java
if(root == null){
    return null;
}
```

---

### Step 2

If the current node matches either `n1` or `n2`, return the current node.

```java
if(root.data == n1 || root.data == n2){
    return root;
}
```

---

### Step 3

Recursively search in the left subtree.

```java
Node leftLca = lca2(root.left, n1, n2);
```

---

### Step 4

Recursively search in the right subtree.

```java
Node rightLca = lca2(root.right, n1, n2);
```

---

### Step 5

#### Case 1

If the left subtree doesn't contain any target node:

```java
if(leftLca == null){
    return rightLca;
}
```

---

#### Case 2

If the right subtree doesn't contain any target node:

```java
if(rightLca == null){
    return leftLca;
}
```

---

#### Case 3

If both left and right return non-null values, then the current node is the LCA.

```java
return root;
```

---

# 🔍 Dry Run

Find LCA of **4** and **7**

```
          1
        /   \
       2     3
      / \   / \
     4   5 6   7
```

### Traversal

```
lca2(1)

Left subtree → returns 4

Right subtree → returns 7

Both are non-null

Return 1
```

Answer:

```
1
```

---

# ⏱ Time Complexity

```
O(n)
```

Each node is visited only once.

---

# 📦 Space Complexity

```
O(h)
```

Where

- `h` = Height of the Binary Tree

This space is due to recursion stack.

Worst Case:

```
O(n)
```

Balanced Tree:

```
O(log n)
```

---

# ✅ Why is Approach 2 Better?

| Approach 1 | Approach 2 |
|------------|------------|
| Stores complete paths | No path storage |
| Extra Space = O(n) | Extra Space = O(h) |
| Traverses tree multiple times | Single traversal |
| Less efficient | More efficient |
| Easy to understand | Optimized solution |

---

# 📌 Key Points

- Uses recursion.
- No extra arrays are required.
- Traverses each node only once.
- Returns the LCA directly.
- Best approach for interviews.

---

# ✅ Complete Java Code

```java
import java.util.*;

public class file {

    static class Node {
        int data;
        Node left, right;

        public Node(int data) {
            this.data = data;
            this.right = null;
            this.left = null;
        }
    }

    // Approach 1 (Using Path)
    public static boolean getPath(Node root, int n, ArrayList<Node> path) {
        if (root == null) {
            return false;
        }

        path.add(root);

        if (root.data == n) {
            return true;
        }

        boolean foundleft = getPath(root.left, n, path);
        boolean foundright = getPath(root.right, n, path);

        if (foundleft || foundright) {
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

    // Approach 2 (Optimized Recursive)
    public static Node lca2(Node root, int n1, int n2) {

        if (root == null) {
            return null;
        }

        if (root.data == n1 || root.data == n2) {
            return root;
        }

        Node leftLca = lca2(root.left, n1, n2);
        Node rightLca = lca2(root.right, n1, n2);

        if (rightLca == null) {
            return leftLca;
        }

        if (leftLca == null) {
            return rightLca;
        }

        return root;
    }

    public static void main(String args[]) {

        Node root = new Node(1);
        root.left = new Node(2);
        root.right = new Node(3);
        root.left.left = new Node(4);
        root.right.right = new Node(7);
        root.left.right = new Node(5);
        root.right.left = new Node(6);

        int n1 = 4, n2 = 7;

        System.out.println(lca2(root, n1, n2).data);
    }
}
```

---

# 🎯 Interview Tips

- Remember the three base cases:
  1. `root == null`
  2. `root == n1`
  3. `root == n2`
- If both recursive calls return non-null, the current node is the LCA.
- If only one side returns non-null, propagate that node upward.
- Time Complexity: **O(n)**
- Space Complexity: **O(h)**
