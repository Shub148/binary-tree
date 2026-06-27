# binary-tree

# 🌳 Binary Tree

## 📖 Definition

A **Binary Tree** is a hierarchical data structure in which each node has **at most two children**:

* Left Child
* Right Child

The topmost node is called the **Root**, and nodes without children are called **Leaf Nodes**.

---

# Structure of a Binary Tree

```text
           Root
             1
           /   \
          2     3
         / \   / \
        4   5 6   7
```

---

# Terminology

| Term          | Description                                  |
| ------------- | -------------------------------------------- |
| Root          | The first node of the tree.                  |
| Parent        | A node having one or more children.          |
| Child         | A node connected below its parent.           |
| Sibling       | Nodes having the same parent.                |
| Leaf Node     | A node with no children.                     |
| Internal Node | A node having at least one child.            |
| Edge          | Connection between two nodes.                |
| Level         | Distance from the root (Root = Level 1).     |
| Height        | Longest path from the node to a leaf.        |
| Depth         | Distance of a node from the root.            |
| Subtree       | Tree formed by any node and its descendants. |

---

# Properties of Binary Tree

### Maximum Nodes at Level L

```text
2^(L-1)
```

Example

```text
Level 1 → 1 Node
Level 2 → 2 Nodes
Level 3 → 4 Nodes
Level 4 → 8 Nodes
```

---

### Maximum Nodes in Height H

```text
2^H - 1
```

Example

```text
Height = 3

Maximum Nodes = 2³ - 1 = 7
```

---

### Minimum Height

```text
⌈log₂(N + 1)⌉
```

where **N** is the number of nodes.

---

# Types of Binary Trees

## 1. Full Binary Tree

Every node has either **0 or 2 children**.

```text
        1
       / \
      2   3
     / \
    4   5
```

---

## 2. Complete Binary Tree

All levels are completely filled except possibly the last level, which is filled from **left to right**.

```text
        1
       / \
      2   3
     / \  /
    4  5 6
```

---

## 3. Perfect Binary Tree

All internal nodes have **2 children** and all leaf nodes are at the same level.

```text
        1
       / \
      2   3
     / \ / \
    4 5 6  7
```

---

## 4. Balanced Binary Tree

The height difference between the left and right subtrees of every node is at most **1**.

Example:

* AVL Tree
* Red-Black Tree

---

## 5. Degenerate (Skewed) Binary Tree

Every node has only one child.

Left Skewed

```text
    1
   /
  2
 /
3
```

Right Skewed

```text
1
 \
  2
   \
    3
```

---

# Binary Tree Representation in Java

```java
class Node {
    int data;
    Node left;
    Node right;

    Node(int data) {
        this.data = data;
        left = null;
        right = null;
    }
}
```

---

# Creating a Binary Tree

```java
Node root = new Node(1);

root.left = new Node(2);
root.right = new Node(3);

root.left.left = new Node(4);
root.left.right = new Node(5);

root.right.left = new Node(6);
root.right.right = new Node(7);
```

Tree

```text
          1
        /   \
       2     3
      / \   / \
     4   5 6   7
```

---

# Binary Tree Traversals

## 1. Preorder (Root → Left → Right)

```text
1 2 4 5 3 6 7
```

---

## 2. Inorder (Left → Root → Right)

```text
4 2 5 1 6 3 7
```

---

## 3. Postorder (Left → Right → Root)

```text
4 5 2 6 7 3 1
```

---

## 4. Level Order (Breadth First Search)

```text
1 2 3 4 5 6 7
```

---

# Common Binary Tree Problems

* Height of Binary Tree
* Count Nodes
* Sum of Nodes
* Diameter of Binary Tree
* Kth Level Nodes
* Lowest Common Ancestor (LCA)
* Top View
* Bottom View
* Left View
* Right View
* Mirror Binary Tree
* Check Balanced Tree
* Subtree of Another Tree

---

# Applications

* Expression Trees
* File System Hierarchy
* Decision Trees
* Syntax Trees (Compilers)
* Artificial Intelligence
* Database Indexing
* Network Routing
* Huffman Coding

---

# Time Complexity of Traversals

| Traversal   | Time Complexity | Space Complexity |
| ----------- | --------------- | ---------------- |
| Preorder    | O(n)            | O(h)             |
| Inorder     | O(n)            | O(h)             |
| Postorder   | O(n)            | O(h)             |
| Level Order | O(n)            | O(n)             |

Where:

* **n** = Number of nodes
* **h** = Height of the tree

---

# Advantages

* Fast searching and traversal.
* Hierarchical data representation.
* Easy recursive implementation.
* Efficient for many divide-and-conquer algorithms.

---

# Disadvantages

* Can become skewed, reducing efficiency.
* Recursive implementation uses stack memory.
* Searching is O(n) in a normal binary tree (unless it is a Binary Search Tree).

---

# Key Points

* Every node has **at most two children**.
* Root is the topmost node.
* Leaf nodes have no children.
* Maximum nodes at level **L = 2^(L−1)**.
* Maximum nodes in a tree of height **H = 2^H − 1**.
* Traversals include **Preorder, Inorder, Postorder, and Level Order**.
* Binary Trees are the foundation for advanced data structures such as **Binary Search Trees (BST), AVL Trees, Heaps, Segment Trees, and Expression Trees**.
