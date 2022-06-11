## Maximum Product of Three Numbers (Leetcode 628)

```cpp
// time complexity: O(1), space: O(1)

class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        
        int optionA = nums[n - 1] * nums[n - 2] * nums[n - 3];
        int optionB = nums[0] * nums[1] * nums[n - 1];
        
        return optionA > optionB ? optionA : optionB;
    }
};
```
