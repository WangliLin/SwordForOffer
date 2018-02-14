### 从上往下打印二叉树

#### 题目
> 从上往下打印出二叉树的每个节点，同层节点从左至右打印。

#### 思路
该题目可转化为二叉树的层次遍历问题，借助一个队列实现即可。

或者也可将其理解为是一道BFS题。对二叉树进行广度优先搜索。

```java
import java.util.*;
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
        ArrayList<Integer> result = new ArrayList<Integer>();
        if (root == null) {
            return result;
        }
        
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            TreeNode treeNode = queue.poll();
            if (treeNode.left != null) {
                queue.offer(treeNode.left);
            }
            if (treeNode.right != null) {
                queue.offer(treeNode.right);
            }
            result.add(treeNode.val);
        }
        
        return result;
    }
}
```