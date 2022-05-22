1. Find the duplicate number.

``` c++
// method 1: count the frequency of every element
// time complexity: O(n), space: O(n)
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int count[nums.size()];
        fill(count, count + nums.size(), 0);
        
        for (int i = 0; i < nums.size(); i++) {
            count[nums[i] - 1]++;
        }
        
        for (int i = 0; i < nums.size(); i++) {
            if (count[i] > 1) {
                return i + 1;
            }
        }
        
        // will never reach this part of the code
        return -1;
    }   
};
```

``` c++
// method 2: using sorting
// time: O(nlogn)

class Solution {
public:
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

``` c++
// method 3: using unordered_set
// time: O(n), space: O(n)

class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        unordered_set <int> s;
        
        for (int i = 0; i < nums.size(); i++) {
            if (s.find(nums[i]) != s.end())
                return nums[i];
            
            s.insert(nums[i]);
        }
        
        return -1;
    }   
};
```

```c++
// method 4: modifying the array
// time complexity: O(n)
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        for (int i = 0; i < nums.size(); i++) {
            if (nums[abs(nums[i]) - 1] < 0)  return abs(nums[i]);
            else  nums[abs(nums[i]) - 1] *= -1;
        }
        
        return -1;
    }   
};
```
