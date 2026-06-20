### 日期：2026/06/20
### 題目：[1840. Maximum Building Height](https://leetcode.com/problems/maximum-building-height/submissions/2040195393/?envType=daily-question&envId=2026-06-20)
#### 難度：Hard
### 解題策略
--
#### 核心思想：兩次掃描約束傳遞法 (Two-Pass Constraint Propagation) 與峰值計算
只需要關注有被限制的建築物（以及頭尾兩棟），因為最大高度必定出現在兩個限制點之間的山峰

### 程式碼
```cpp=
class Solution {
public:
    int maxBuilding(int n,vector<vector<int>>& restrictions) {
        restrictions.push_back({1,0});
        sort(restrictions.begin(),restrictions.end());
        if(restrictions.back()[0]!=n){
            restrictions.push_back({n,n-1});
        }

        int m=restrictions.size();

        for(int i=1;i<m;i++){
            int dist=restrictions[i][0]-restrictions[i-1][0];

            restrictions[i][1]=min(restrictions[i][1],restrictions[i-1][1]+dist);
        }

        for(int i=m-2;i>=0;i--){
            int dist=restrictions[i+1][0]-restrictions[i][0];
            restrictions[i][1]=min(restrictions[i][1],restrictions[i+1][1]+dist);
        }

        int max_height=0;
        for(int i=1;i<m;++i){
            int dist = restrictions[i][0] - restrictions[i-1][0];
            int h1 = restrictions[i-1][1];
            int h2 = restrictions[i][1];

            int local_max=(h1+h2+dist)/2;
            max_height = max(max_height,local_max);
        }
        return max_height;
        

    }
};
```
