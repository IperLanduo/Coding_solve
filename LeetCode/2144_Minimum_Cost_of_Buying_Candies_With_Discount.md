### 2006 / 06 / 02
### 題目：[2144. Minimum Cost of Buying Candies With Discount](https://leetcode.com/problems/minimum-cost-of-buying-candies-with-discount/description/?envType=daily-question&envId=2026-06-01)
#### 難度：Easy
### 解題策略
就是單純使用`sort`去進行**由大到小**的排列即可，但需要預防 `out of range`

### 程式碼
```cpp=
class Solution {
public:
    int minimumCost(vector<int>& cost) {
        int n,ans=0;
        n = cost.size();

        sort(cost.begin(),cost.end(),greater<int>());

        for(int i=0; i<n;i+=3){
            ans += cost[i];
            if(i+1<n)ans += cost[i+1];
        }
        return ans;

    }
};
```

