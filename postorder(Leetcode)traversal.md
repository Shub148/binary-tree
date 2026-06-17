# 145. Binary Tree Postorder Traversal (LeetCode)

## Problem

Given the root of a binary tree, return the postorder traversal of its nodes' values.

### Postorder Traversal Order

```text
Left -> Right -> Root
```

## Java Solution (Recursive)

```java
class Solution {
    List<Integer> ans = new ArrayList<>();

    public List<Integer> postorderTraversal(TreeNode root) {
        postorder(root);
        return ans;
    }

    private void postorder(TreeNode root) {
        if (root == null) {
            return;
        }

        postorder(root.left);
        postorder(root.right);
        ans.add(root.val);
    }
}
```

## Explanation

1. Traverse the left subtree.
2. Traverse the right subtree.
3. Visit the root node and add its value to the list.

### Example

Input:

```text
    1
   / \
  2   3
```

Output:

```text
[2, 3, 1]
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
