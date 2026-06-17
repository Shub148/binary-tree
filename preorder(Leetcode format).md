# Binary Tree Preorder Traversal (LeetCode Format)

```java
import java.util.*;

class Solution {

    List<Integer> ans = new ArrayList<>();

    public List<Integer> preorderTraversal(TreeNode root) {
        preorder(root);
        return ans;
    }

    private void preorder(TreeNode root) {
        if (root == null) {
            return;
        }

        ans.add(root.val);
        preorder(root.left);
        preorder(root.right);
    }
}
```

### Changes from My Original Code

| My Code            | LeetCode                   |
| ------------------ | -------------------------- |
| Node               | TreeNode                   |
| data               | val                        |
| System.out.print() | ans.add()                  |
| main() method      | Not required               |
| buildTree()        | LeetCode provides the tree |

### Time Complexity

* O(n)

### Space Complexity

* O(h)
* h = height of tree

```
```
