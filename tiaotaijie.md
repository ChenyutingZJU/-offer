# 跳台阶
### 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

### 解题思路
因为一次可以跳1级，也可以跳2级，所以有`f(n)=f(n-1)+f(n-2)`，所以和斐波那契数列同样的思路，可以递归也可以递推。

```
class Solution {
public:
    int jumpFloor(int number) {
        if(number<=2) return number;
        int a=1,b=2,c;
        for(int i=3;i<=number;i++){
            c=a+b;
            a=b;
            b=c;
        }
        return c;
    }
};
```

