# Inorder Traversal in Binary Tree (Java)

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

        public static void inorder(Node root) {
            if (root == null) {
                return;
            }

            inorder(root.left);
            System.out.print(root.data + " ");
            inorder(root.right);
        }
    }

    public static void main(String args[]) {
        int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};

        BinaryTree tree = new BinaryTree();
        Node root = tree.buildTree(node);

        tree.inorder(root);
    }
}
```

---

# What is Inorder Traversal?

Inorder Traversal visits nodes in the following order:

```text
Left → Root → Right
```

This means:

1. Visit the left subtree.
2. Process the current node.
3. Visit the right subtree.

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

# Inorder Method

```java
public static void inorder(Node root) {
    if (root == null) {
        return;
    }

    inorder(root.left);
    System.out.print(root.data + " ");
    inorder(root.right);
}
```

---

# Step-by-Step Execution

### Start

```java
inorder(1)
```

Move to the left subtree.

### Visit Node 2

```java
inorder(2)
```

Again move left.

### Visit Node 4

```java
inorder(4)
```

Left child is null.

Print:

```text
4
```

Right child is null.

---

### Back to Node 2

Print:

```text
2
```

Move to right child (5).

---

### Visit Node 5

Print:

```text
5
```

---

### Back to Node 1

Print:

```text
1
```

Move to right subtree.

---

### Visit Node 3

Left child is null.

Print:

```text
3
```

Move to right child (6).

---

### Visit Node 6

Print:

```text
6
```

---

# Traversal Sequence

```text
4 → 2 → 5 → 1 → 3 → 6
```

---

# Output

```text
4 2 5 1 3 6
```

---

# Dry Run

```text
inorder(1)
│
├── inorder(2)
│   │
│   ├── inorder(4)
│   │   ├── null
│   │   ├── print 4
│   │   └── null
│   │
│   ├── print 2
│   │
│   └── inorder(5)
│       ├── null
│       ├── print 5
│       └── null
│
├── print 1
│
└── inorder(3)
    │
    ├── null
    ├── print 3
    │
    └── inorder(6)
        ├── null
        ├── print 6
        └── null
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

where `h` is the height of the tree.

* Balanced Tree → O(log n)
* Skewed Tree → O(n)

---

# Key Points

* Inorder Traversal follows **Left → Root → Right**.
* Uses recursion to visit every node.
* For a Binary Search Tree (BST), inorder traversal gives elements in sorted order.
* Time Complexity: **O(n)**.
* Space Complexity: **O(h)**.
