Here's a clean set of **notes for Diameter of a Binary Tree – Approach 1** that you can keep in your DSA repository.

# Diameter of a Binary Tree (Approach 1)

## Definition

The **diameter** of a binary tree is the **number of nodes on the longest path between any two nodes** in the tree.

### Example

```text
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

Longest path:

```text
4 → 2 → 1 → 3 → 7
```

Diameter = **5 nodes**

---

## Idea

For every node:

1. Find the diameter of the left subtree.
2. Find the diameter of the right subtree.
3. Find the height of the left subtree.
4. Find the height of the right subtree.
5. Calculate:

```text
Diameter through current node
= Left Height + Right Height + 1
```

6. Return the maximum among:

```text
max(
    selfDiameter,
    leftDiameter,
    rightDiameter
)
```

---

## Formula

```text
Diameter(Node) =
max(
    Left Height + Right Height + 1,
    Left Diameter,
    Right Diameter
)
```

---

## Algorithm

```text
diameter(root)

If root == null
    return 0

leftDiameter = diameter(root.left)
rightDiameter = diameter(root.right)

leftHeight = height(root.left)
rightHeight = height(root.right)

selfDiameter = leftHeight + rightHeight + 1

return maximum of
(selfDiameter, leftDiameter, rightDiameter)
```

---

## Dry Run

For node 1:

```text
Left Height = 2
Right Height = 2

Self Diameter
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

### Height Function

```java
height(root)
```

takes:

```text
O(n)
```

### Diameter Function

For every node, height is calculated again and again.

```text
Diameter = O(n²)
```

### Space Complexity

Recursive stack:

```text
O(h)
```

where `h` is the height of the tree.

Worst case:

```text
O(n)
```

---

## Drawback of Approach 1

This approach recalculates the height of subtrees many times.

Example:

```text
height(node)
```

is computed repeatedly for different recursive calls.

Hence:

```text
Time Complexity = O(n²)
```

---

## Conclusion

* Easy to understand and implement.
* Uses separate `height()` and `diameter()` functions.
* Recomputes heights multiple times.
* Time Complexity: **O(n²)**.
* Can be optimized to **O(n)** using Diameter Approach 2 (height and diameter calculated together).
