# Level Order Traversal in Binary Tree (Java)

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

        public static void levelorder(Node root) {
            if (root == null) {
                return;
            }

            Queue<Node> q = new LinkedList<>();
            q.add(root);
            q.add(null);

            while (!q.isEmpty()) {
                Node currNode = q.remove();

                if (currNode == null) {
                    System.out.println();

                    if (q.isEmpty()) {
                        break;
                    } else {
                        q.add(null);
                    }
                } else {
                    System.out.print(currNode.data + " ");

                    if (currNode.left != null) {
                        q.add(currNode.left);
                    }

                    if (currNode.right != null) {
                        q.add(currNode.right);
                    }
                }
            }
        }
    }

    public static void main(String args[]) {
        int node[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};

        BinaryTree tree = new BinaryTree();
        Node root = tree.buildTree(node);

        tree.levelorder(root);
    }
}
```

---

# What is Level Order Traversal?

Level Order Traversal visits nodes level by level from top to bottom.

It is also known as:

```text
Breadth First Search (BFS)
```

Traversal order:

```text
Level 1 → Level 2 → Level 3 → ...
```

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

# Level Order Method

```java
public static void levelorder(Node root) {
    if (root == null) {
        return;
    }

    Queue<Node> q = new LinkedList<>();

    q.add(root);
    q.add(null);

    while (!q.isEmpty()) {
        Node currNode = q.remove();

        if (currNode == null) {
            System.out.println();

            if (q.isEmpty()) {
                break;
            } else {
                q.add(null);
            }
        } else {
            System.out.print(currNode.data + " ");

            if (currNode.left != null) {
                q.add(currNode.left);
            }

            if (currNode.right != null) {
                q.add(currNode.right);
            }
        }
    }
}
```

---

# How It Works

### Step 1: Create Queue

```java
Queue<Node> q = new LinkedList<>();
```

A queue is used because Level Order Traversal follows the FIFO (First In First Out) principle.

---

### Step 2: Add Root and Null Marker

```java
q.add(root);
q.add(null);
```

* `root` starts the traversal.
* `null` marks the end of a level.

Queue:

```text
[1, null]
```

---

### Step 3: Remove Elements One by One

```java
Node currNode = q.remove();
```

The front node is removed and processed.

---

### Step 4: Process Null Marker

```java
if(currNode == null)
```

When a null marker is found:

```java
System.out.println();
```

Move to the next line.

If the queue is not empty:

```java
q.add(null);
```

Add another marker for the next level.

---

### Step 5: Process Normal Node

```java
System.out.print(currNode.data + " ");
```

Print the current node.

---

### Step 6: Add Children

```java
if(currNode.left != null)
    q.add(currNode.left);

if(currNode.right != null)
    q.add(currNode.right);
```

Insert left and right children into the queue.

---

# Dry Run

### Initial Queue

```text
[1, null]
```

---

### Process Level 1

Remove 1

Print:

```text
1
```

Add children:

```text
[null, 2, 3]
```

---

### End of Level 1

Remove null

Print new line

Queue:

```text
[2, 3, null]
```

---

### Process Level 2

Remove 2

Print:

```text
2
```

Add children 4 and 5

Queue:

```text
[3, null, 4, 5]
```

Remove 3

Print:

```text
3
```

Add child 6

Queue:

```text
[null, 4, 5, 6]
```

---

### End of Level 2

Remove null

Print new line

Queue:

```text
[4, 5, 6, null]
```

---

### Process Level 3

Print:

```text
4 5 6
```

Queue becomes:

```text
[null]
```

Remove null and stop.

---

# Traversal Order

```text
Level 1 : 1
Level 2 : 2 3
Level 3 : 4 5 6
```

---

# Output

```text
1
2 3
4 5 6
```

---

# Queue Visualization

```text
Start:
[1, null]

After processing 1:
[null, 2, 3]

After level 1:
[2, 3, null]

After processing 2:
[3, null, 4, 5]

After processing 3:
[null, 4, 5, 6]

After level 2:
[4, 5, 6, null]

After level 3:
[null]

End:
[]
```

---

# Time Complexity

### Time Complexity

```text
O(n)
```

Each node is visited exactly once.

---

### Space Complexity

```text
O(n)
```

The queue may store an entire level of nodes.

---

# Key Points

* Level Order Traversal is also called **Breadth First Search (BFS)**.
* Uses a Queue data structure.
* Nodes are visited level by level.
* `null` is used as a level separator.
* Time Complexity: **O(n)**.
* Space Complexity: **O(n)**.
* Commonly used in:

  * Shortest path problems
  * Tree serialization
  * Network traversal
  * Finding tree levels
  * BFS-based algorithms

---

# Final Output

```text
1
2 3
4 5 6
```
