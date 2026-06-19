### 日期：2026/06/18
### 題目：[1344. Angle Between Hands of a Clock](https://leetcode.com/problems/angle-between-hands-of-a-clock/description/?envType=daily-question&envId=2026-06-18)
#### 難度：Mid
### 解題策略
除了基本的角度轉換，還要注意時針會隨著分鐘移動
以及答案是要比較小的夾角
### 程式碼
```cpp=
class Solution {
public:
    double angleClock(int hour, int minutes) {
        double ans = 0;
        double m = minutes*6;
        double h = (hour%12)*30 + minutes*0.5;
        ans = abs(h-m);
        return min(ans, 360-ans);

    }   
};
```
