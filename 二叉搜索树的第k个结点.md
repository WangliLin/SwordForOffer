### 二叉搜索树的第k个结点

#### 题目
>  给定一颗二叉搜索树，请找出其中的第k大的结点。例如， 5 / \ 3 7 /\ /\ 2 4 6 8 中，按结点数值大小顺序第三个结点的值为4。

#### 思路
 - 主要思想：递归，中序遍历
 - 题目要点：
	 - 要得到第k大的节点，首先需要对二叉搜索树进行中序遍历。

#### 代码

```java
/*
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
    int index = 0;
    TreeNode KthNode(TreeNode pRoot, int k)
    {
        if (pRoot != null) {
            TreeNode node = KthNode(pRoot.left, k);
            if (node != null)
                return node;
            index++;
            if (index == k)
                return pRoot;
            node = KthNode(pRoot.right, k);
            if (node != null)
                return node;
        }
        return null;
    }


}
```