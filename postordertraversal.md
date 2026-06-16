# Postorder Traversal in Binary Tree (Java)

## Complete Code

```java
import java.util.*;

class file {
    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
            this.left = null;
            this.right = null;
        }
    }

    static class BinaryTree {
        static int index = -1;

        public static Node buildTree(int node[]) {
            index++;

            if (node[index] == -1) {
                return null;
            }

            Node newNode = new Node(node[index]);

            newNode.left = buildTree(node);
            newNode.right = buildTree(node);

            return newNode;
        }

        public static void postorder(Node root) {
            if (root == null) {
                return;
            }

            postorder(root.left);
            postorder(root.right);
            System.out.print(root.data + " ");
        }
    }

    public static void main(String args[]) {
        int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};

        BinaryTree tree = new BinaryTree();
        Node root = tree.buildTree(node);

        tree.postorder(root);
    }
}
```

---

# What is Postorder Traversal?

Postorder Traversal visits nodes in the following order:

```text
Left → Right → Root
```

This means:

1. Visit the left subtree.
2. Visit the right subtree.
3. Process the current node.

---

# Binary Tree Created

The preorder array:

```java
{1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1}
```

creates the following tree:

```text
        1
       / \
      2   3
     / \   \
    4   5   6
```

---

# Postorder Method

```java
public static void postorder(Node root) {
    if (root == null) {
        return;
    }

    postorder(root.left);
    postorder(root.right);
    System.out.print(root.data + " ");
}
```

---

# How It Works

### Step 1: Check for Null

```java
if (root == null) {
    return;
}
```

If the current node is `null`, stop recursion and return.

---

### Step 2: Traverse Left Subtree

```java
postorder(root.left);
```

Visit all nodes in the left subtree.

---

### Step 3: Traverse Right Subtree

```java
postorder(root.right);
```

Visit all nodes in the right subtree.

---

### Step 4: Visit Root Node

```java
System.out.print(root.data + " ");
```

Print the current node after visiting both subtrees.

---

# Step-by-Step Execution

### Start

```java
postorder(1)
```

Move to the left subtree.

### Visit Node 4

Print:

```text
4
```

---

### Visit Node 5

Print:

```text
5
```

---

### Back to Node 2

Print:

```text
2
```

---

### Visit Node 6

Print:

```text
6
```

---

### Back to Node 3

Print:

```text
3
```

---

### Back to Root Node 1

Print:

```text
1
```

---

# Traversal Sequence

```text
4 → 5 → 2 → 6 → 3 → 1
```

---

# Output

```text
4 5 2 6 3 1
```

---

# Dry Run

```text
postorder(1)
│
├── postorder(2)
│   │
│   ├── postorder(4)
│   │   ├── null
│   │   ├── null
│   │   └── print 4
│   │
│   ├── postorder(5)
│   │   ├── null
│   │   ├── null
│   │   └── print 5
│   │
│   └── print 2
│
├── postorder(3)
│   │
│   ├── null
│   │
│   ├── postorder(6)
│   │   ├── null
│   │   ├── null
│   │   └── print 6
│   │
│   └── print 3
│
└── print 1
```

---

# Time Complexity

### Time Complexity

```text
O(n)
```

Every node is visited exactly once.

### Space Complexity

```text
O(h)
```

Where `h` is the height of the tree.

* Balanced Tree → `O(log n)`
* Skewed Tree → `O(n)`

---

# Key Points

* Postorder Traversal follows **Left → Right → Root**.
* The root node is processed after both subtrees are visited.
* Uses recursion to visit every node exactly once.
* Time Complexity: **O(n)**.
* Space Complexity: **O(h)**.
* Commonly used for:

  * Deleting a tree
  * Expression tree evaluation
  * Directory traversal
  * Memory cleanup operations

---

# Final Output

```text
4 5 2 6 3 1
```
