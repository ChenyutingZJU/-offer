# 和为S的连续正数序列
### 题目描述
小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!
**输出描述:**
输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

### 解题思路
* 因为是连续的正数序列，所以可以用两个指针，计算两个指针内数列的和。
* 等于S就把两个指针区间内的数字加入到结果中。如果小于S，则右指针移动，表示加入一个元素，如果大于S，左指针移动，表示减去一个元素
* 因为至少要两个数，所以当左指针超过S/2时，就停止

```
class Solution {
public:
    vector<vector<int> > FindContinuousSequence(int sum) {
        vector<int>tmp;
        vector<vector<int>>ans;
        if(sum<3) return ans;
        int left=1,right=2,mid=(sum+1)>>1;
        while(left<mid){
            //序列的和
            int k=(left+right)*(right-left+1)/2;
            if(k==sum){
                for(int i=left;i<=right;i++){
                    tmp.push_back(i);
                }
                ans.push_back(tmp);
                tmp.clear();
                left++;
                right++;
            }else if(k<sum){
                right++;
            }else{
                left++;
            }
        }
        return ans;
    }
};
```

