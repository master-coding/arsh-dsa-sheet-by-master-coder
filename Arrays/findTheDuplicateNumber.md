1. Find the duplicate number.

    1. Method1: Using sorting.
        - Time complexity: O(nlogn)

``` c++
class Solution {
public:
    // method 1: using sorting
    // time: O(nlogn)
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] == nums[i - 1]) {
                return nums[i];
            }
        }
        
        // will never reach this part of code
        return nums[nums.size() - 1];
    }
    
    
};
```
