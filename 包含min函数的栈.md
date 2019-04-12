# 包含min函数的栈
### 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

### 解题思路
* 需要一个普通栈和一个最小栈，最小栈的栈顶总是记录当前普通栈中的最小元素
* `top`的时候，直接取普通栈顶、最小栈顶的元素即可
* `pop`的时候，要先判断栈非空，然后将普通栈和最小站同时`pop`
* `push`的时候，普通栈直接`push`，最小栈需要跟栈顶元素比较，将其中更小的那个`push`进去
* 始终要注意对栈非空的判断

```
class Solution {
public:
    void push(int value) {
        st.push(value);
        //注意，判断栈非空的语句要在最前面
        if(minst.empty() || value<minst.top())
            minst.push(value);
        else
            minst.push(minst.top());
    }
    void pop() {
        if(!st.empty()){
            st.pop();
            minst.pop();
        }
    }
    int top() {
        return st.top();
    }
    int min() {
        return minst.top();
    }
private:
    stack<int>st,minst;
};
```

