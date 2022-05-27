## Two Sum

```cpp
// time complexity: O(n**2), auxillary space: O(1)

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for (int i = 0; i < nums.size(); i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[i] + nums[j] == target)
                    return {i, j};
            }
        }
        
        return {};
    }
};
```

```cpp
// time complexity: O(n), auxillary space: O(n)

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map <int, int> m;

        for (int i = 0; i < nums.size(); i++) {
            if (m.count(target - nums[i])) return {i, m[target - nums[i]]};
            else m[nums[i]] = i;
        }

        return {};
    }
};
```
