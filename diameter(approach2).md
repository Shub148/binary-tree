# Diameter of a Binary Tree (Approach 2 - Optimized)

## Definition

The **diameter** of a binary tree is the number of nodes on the longest path between any two nodes in the tree.

Example:

```text
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

Longest Path:

```text
4 → 2 → 1 → 3 → 7
```

Diameter = **5 Nodes**

---

## Problem with Approach 1

In Approach 1, for every node we calculate:

* Height of left subtree
* Height of right subtree
* Diameter of left subtree
* Diameter of right subtree

Since height is calculated repeatedly, the time complexity becomes:

```text
O(n²)
```

---

## Optimized Idea (Approach 2)

Calculate **Height** and **Diameter** together in a single traversal.

For every node, return:

1. Height of subtree
2. Diameter of subtree

This avoids repeated height calculations.

---

## Helper Class

```java
static class info {
    int diam;
    int height;

    public info(int diam, int height) {
        this.diam = diam;
        this.height = height;
    }
}
```

### Purpose

The `info` class stores:

* `diam` → Diameter of the subtree
* `height` → Height of the subtree

---

## Algorithm

### Base Case

```java
if(root == null){
    return new info(0,0);
}
```

For a null node:

* Height = 0
* Diameter = 0

---

### Recursive Calls

```java
info leftinfo = diameter2(root.left);
info rightinfo = diameter2(root.right);
```

Get information from left and right subtrees.

---

### Calculate Diameter

Three possibilities:

1. Diameter lies completely in left subtree.
2. Diameter lies completely in right subtree.
3. Diameter passes through current node.

```java
int diam = Math.max(
                Math.max(leftinfo.diam, rightinfo.diam),
                leftinfo.height + rightinfo.height + 1
           );
```

---

### Calculate Height

```java
int height = Math.max(leftinfo.height, rightinfo.height) + 1;
```

---

### Return Result

```java
return new info(diam, height);
```

---

## Dry Run

For the tree:

```text
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

At Root Node (1):

```text
Left Height  = 2
Right Height = 2

Diameter Through Root
= 2 + 2 + 1
= 5
```

Left Diameter = 3

Right Diameter = 3

```text
Diameter = max(5, 3, 3)
         = 5
```

Output:

```text
5
```

---

## Complexity Analysis

### Time Complexity

Each node is visited only once.

```text
O(n)
```

### Space Complexity

Recursive stack space:

```text
O(h)
```

Where:

* `h` = Height of Tree

Worst Case (Skewed Tree):

```text
O(n)
```

---

## Comparison

| Approach   | Time Complexity | Space Complexity |
| ---------- | --------------- | ---------------- |
| Approach 1 | O(n²)           | O(h)             |
| Approach 2 | O(n)            | O(h)             |

---

## Key Insight

Instead of calculating height separately for every node, store height and diameter together in an object and return both during recursion.

This reduces the time complexity from:

```text
O(n²) → O(n)
```

making Approach 2 the optimized solution for finding the diameter of a binary tree.
