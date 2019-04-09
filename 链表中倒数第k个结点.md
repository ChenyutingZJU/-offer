# 链表中倒数第k个结点
### 题目描述
输入一个链表，输出该链表中倒数第k个结点。

### 解题思路
* 首先判断链表是否为空
* 再要考虑k大于链表长度的情况
* 双指针法，p指针先走k-1步，然后再p、q指针一起走，当p指针到头，q指向的就是倒数第k个结点。
* 可以先遍历一趟求出链表长度，对k取余，保证k不超过链表长度
* 也可以只遍历一次，如果k超过链表长度，那么p到链表尾时，用于计数的cnt还是小于k的。

```
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if(pListHead==NULL) return pListHead;
        ListNode *p=pListHead,*q=pListHead;
        int cnt=0;
        while(p){
            if(cnt<k){
                cnt++;
            }else{
                q=q->next;
            }
            p=p->next;
        }
        return cnt<k?NULL:q;
    }
};
```

