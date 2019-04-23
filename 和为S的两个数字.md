# 和为S的两个数字
### 题目描述
输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。
**输出描述:**
对应每个测试案例，输出两个数，小的先输出。

### 解题思路
* 双指针法，分别从头和尾开始，取两个数字的和
* 如果和小于S，左指针+1；如果大于S，右指针+1
* 因为要求两个数的乘积也最小，也就是两个数差得大一点，所以一旦找到和为S的两个数，就直接结束

```
class Solution {
public:
    vector<int> FindNumbersWithSum(vector<int> array,int sum) {
        vector<int>ans;
        int i=0,j=array.size()-1;
        while(i<=j){
            if(array[i]+array[j]==sum){
                ans.push_back(array[i]);
                ans.push_back(array[j]);
                break;
            }else if(array[i]+array[j]>sum){
                j--;
            }else{
                i++;
            }
        }
        return ans;
    }
};
```

