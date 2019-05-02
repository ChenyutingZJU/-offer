# 二叉搜索树的第k个节点
### 题目描述
给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）    中，按结点数值大小顺序第三小结点的值为4。

### 解题思路
* 二叉搜索树的中序遍历得到的是有序的序列
* 中序遍历的同时使用一个全局变量记录当前遍历到了第几个数

```
class Solution {
public:
    int index=0;
    TreeNode* KthNode(TreeNode* pRoot, int k)
    {
        //中序遍历二叉树的思想
       if(pRoot!=NULL) {
           //左子树
           TreeNode* ret=KthNode(pRoot->left,k);
           if(ret!=NULL) return ret;
           index++;
           //比较
           if(index==k) return pRoot;
           //右子树
           ret=KthNode(pRoot->right,k);
           if(ret!=NULL) return ret;
       }
       return NULL;
    }
};
```

