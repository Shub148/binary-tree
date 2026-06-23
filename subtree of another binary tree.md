# Subtree of Another Tree (Binary Tree)

## Problem

Given two binary trees `root` and `subroot`, check whether `subroot` is a subtree of `root`.

A subtree of a binary tree is a node in the tree along with all of its descendants.

### Example

**Main Tree**

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

**Subtree**

```
      2
     / \
    4   5
```

**Output**

```
true
```

---

## Approach

We use two recursive functions:

### 1. `isIdentical()`

Checks whether two trees are exactly the same.

**Base Cases**

* Both nodes are `null` → `true`
* One node is `null` or values differ → `false`

**Recursive Check**

* Compare left subtrees.
* Compare right subtrees.

### 2. `isSubtree()`

Checks whether `subroot` exists inside `root`.

**Steps**

1. If `root` is `null`, return `false`.
2. If current node value matches `subroot` value:

   * Call `isIdentical()`.
   * If identical, return `true`.
3. Recursively search in left subtree.
4. Recursively search in right subtree.
5. Return `leftAns || rightAns`.

---

## Code

```java
public static boolean isIdentical(Node node, Node subroot) {
    if (node == null && subroot == null) {
        return true;
    }

    if (node == null || subroot == null ||
        node.data != subroot.data) {
        return false;
    }

    if (!isIdentical(node.left, subroot.left)) {
        return false;
    }

    if (!isIdentical(node.right, subroot.right)) {
        return false;
    }

    return true;
}

public static boolean isSubtree(Node root, Node subroot) {
    if (root == null) {
        return false;
    }

    if (root.data == subroot.data) {
        if (isIdentical(root, subroot)) {
            return true;
        }
    }

    boolean leftAns = isSubtree(root.left, subroot);
    boolean rightAns = isSubtree(root.right, subroot);

    return leftAns || rightAns;
}
```

---

## Dry Run

Current node = `1`

* `1 != 2`, so search left and right.

Current node = `2`

* `2 == 2`
* Call `isIdentical()`

  * `2 == 2`
  * `4 == 4`
  * `5 == 5`
  * Structure also matches

Result → `true`

Therefore, `subroot` is a subtree of `root`.

---

## Time Complexity

### `isIdentical()`

```
O(M)
```

Where `M` = number of nodes in `subroot`.

### `isSubtree()`

For every node of the main tree, we may call `isIdentical()`.

```
O(N × M)
```

Where:

* `N` = nodes in `root`
* `M` = nodes in `subroot`

### Space Complexity

```
O(H)
```

Where `H` is the height of the tree due to recursion stack.
