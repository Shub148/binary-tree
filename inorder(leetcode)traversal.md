# 94. Binary Tree Inorder Traversal (LeetCode)

## Problem

Given the root of a binary tree, return the inorder traversal of its nodes' values.

### Inorder Traversal Order

```text
Left -> Root -> Right
```

## Java Solution (Recursive)

```java
class Solution {
    List<Integer> ans = new ArrayList<>();

    public List<Integer> inorderTraversal(TreeNode root) {
        inorder(root);
        return ans;
    }

    private void inorder(TreeNode root) {
        if (root == null) {
            return;
        }

        inorder(root.left);
        ans.add(root.val);
        inorder(root.right);
    }
}
```

## Explanation

1. Traverse the left subtree.
2. Visit the root node and add its value to the list.
3. Traverse the right subtree.

### Example

Input:

```text
    1
   / \
  2   3
```

Output:

```text
[2, 1, 3]
```

## Time Complexity

```text
O(n)
```

## Space Complexity

```text
O(h)
```

Where:

* n = number of nodes
* h = height of the tree
