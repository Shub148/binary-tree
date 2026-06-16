# Binary Tree Construction Using Preorder Traversal (Java)

## Overview

This program constructs a binary tree from a preorder traversal array where:

* Each integer represents a node value.
* `-1` represents a `null` node (no child).

### Input Array

```java
int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};
```

### Tree Representation

The above preorder sequence creates the following tree:

```text
        1
       / \
      2   3
     / \   \
    4   5   6
```

---

## Node Class

```java
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
```

### Purpose

The `Node` class represents a single node in the binary tree.

### Components

* `data` → stores the node value.
* `left` → reference to the left child.
* `right` → reference to the right child.

---

## BinaryTree Class

```java
static class BinaryTree {
    static int index = -1;
```

### Purpose

The `index` variable tracks the current position in the preorder array while constructing the tree.

---

## buildTree() Method

```java
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
```

### Working

#### Step 1: Move to Next Element

```java
index++;
```

The index is incremented to process the next element in the array.

#### Step 2: Check for Null Node

```java
if (node[index] == -1) {
    return null;
}
```

If the current value is `-1`, there is no node, so return `null`.

#### Step 3: Create New Node

```java
Node newNode = new Node(node[index]);
```

A new node is created with the current value.

#### Step 4: Build Left Subtree

```java
newNode.left = buildTree(node);
```

Recursively construct the left child.

#### Step 5: Build Right Subtree

```java
newNode.right = buildTree(node);
```

Recursively construct the right child.

#### Step 6: Return Root

```java
return newNode;
```

Return the constructed subtree root.

---

## Dry Run

### Preorder Array

```text
1 2 4 -1 -1 5 -1 -1 3 -1 6 -1 -1
```

### Execution Flow

```text
buildTree(1)
│
├── buildTree(2)
│   │
│   ├── buildTree(4)
│   │   ├── null
│   │   └── null
│   │
│   └── buildTree(5)
│       ├── null
│       └── null
│
└── buildTree(3)
    ├── null
    └── buildTree(6)
        ├── null
        └── null
```

---

## Time Complexity

### Time

```text
O(n)
```

Each element of the array is visited exactly once.

### Space

```text
O(h)
```

Where `h` is the height of the tree due to recursive call stack.

* Best Case (Balanced Tree): `O(log n)`
* Worst Case (Skewed Tree): `O(n)`

---

## Output

```java
System.out.println(root.data);
```

### Output

```text
1
```

The root node of the constructed binary tree is `1`.

---

## Key Points

1. Tree is built using **Preorder Traversal** (`Root → Left → Right`).
2. `-1` is used as a marker for `null` nodes.
3. Recursion automatically constructs left and right subtrees.
4. Time Complexity = **O(n)**.
5. Common interview question for Binary Trees and Recursion.

### Full Code

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
    }

    public static void main(String args[]) {
        int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};

        BinaryTree tree = new BinaryTree();
        Node root = tree.buildTree(node);

        System.out.println(root.data);
    }
}
```

# Preorder Traversal in Binary Tree

## Definition

Preorder Traversal follows the order:

```text
Root → Left Subtree → Right Subtree
```

For the constructed tree:

```text
        1
       / \
      2   3
     / \   \
    4   5   6
```

The preorder traversal will be:

```text
1 2 4 5 3 6
```

---

## Preorder Traversal Method

```java
public static void preorder(Node root) {

    if (root == null) {
        return;
    }

    System.out.print(root.data + " ");
    preorder(root.left);
    preorder(root.right);
}
```

---

## How It Works

### Step 1: Check for Null

```java
if (root == null) {
    return;
}
```

If the current node is `null`, stop recursion and return.

---

### Step 2: Visit Root Node

```java
System.out.print(root.data + " ");
```

Print the current node's value before visiting its children.

---

### Step 3: Traverse Left Subtree

```java
preorder(root.left);
```

Recursively visit all nodes in the left subtree.

---

### Step 4: Traverse Right Subtree

```java
preorder(root.right);
```

Recursively visit all nodes in the right subtree.

---

## Dry Run

### Tree

```text
        1
       / \
      2   3
     / \   \
    4   5   6
```

### Recursive Calls

```text
preorder(1)
│
├── print 1
│
├── preorder(2)
│   │
│   ├── print 2
│   │
│   ├── preorder(4)
│   │   ├── print 4
│   │   ├── null
│   │   └── null
│   │
│   └── preorder(5)
│       ├── print 5
│       ├── null
│       └── null
│
└── preorder(3)
    │
    ├── print 3
    │
    ├── null
    │
    └── preorder(6)
        ├── print 6
        ├── null
        └── null
```

---

## Traversal Order

```text
1 → 2 → 4 → 5 → 3 → 6
```

### Output

```text
1 2 4 5 3 6
```

---

## Time Complexity

### Time Complexity

```text
O(n)
```

Every node is visited exactly once.

### Space Complexity

```text
O(h)
```

Where `h` is the height of the tree due to the recursive call stack.

* Balanced Tree → `O(log n)`
* Skewed Tree → `O(n)`

---

## Updated Main Method

```java
public static void main(String args[]) {
    int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};

    BinaryTree tree = new BinaryTree();
    Node root = tree.buildTree(node);

    tree.preorder(root);
}
```

### Complete Output

```text
1 2 4 5 3 6
```

## Key Points

1. Preorder Traversal follows **Root → Left → Right**.
2. The root node is processed before its children.
3. Uses recursion to visit every node.
4. Time Complexity = **O(n)**.
5. Commonly used for:

   * Tree serialization
   * Copying a tree
   * Expression trees
   * Binary tree construction problems
