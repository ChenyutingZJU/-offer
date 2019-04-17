# 最小的k个数
### 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

### 解题思路
* 如果允许修改数组，可使用快速排序中的Partition函数，找到第k个数字，这样他左边的就是我们要的。但是不支持海量数据，因为要把所有数字都读入内存。
* 借用STL中的set模拟堆，因为set内部使用红黑树实现，自动有序、去重。把当前最小的k个数存入set，不断的用新的数字去比对，决定是否替换set中的最后一个数字
* 优点：复杂度是O（nlogk），适合海量数据的输入，即不需要把数据都读入内存，可以每次从磁盘中读入一些数，最小只需要内存能容纳k个数就行，适合于n很大，k较小的问题
* 如果set的容量还没有达到k，直接向里面push
* 否则，判断当前元素和set最后一个元素（也就是其中最大的数），如果比set中最大的元素小，那么删除最后一个元素，把当前元素push，最后遍历完数组，set中存放的就是最小的k个数

```
class Solution {
public:
    vector<int> GetLeastNumbers_Solution(vector<int> input, int k) {
        vector<int>ans;
        if(k<=0 || k>input.size()||input.empty()) return ans;
        int len=input.size();
        for(int i=0;i<len;i++){
            if(s.size()<k){
                s.insert(input[i]);
            }else{
                auto it=s.end();
                it--;
                if(input[i]<*(it)){
                    s.erase(it);
                    s.insert(input[i]);
                }
            }
        }
        for(auto it=s.begin();it!=s.end();it++){
            ans.push_back(*it);
        }
        return ans;
    }
private:
    set<int>s;
};
```

