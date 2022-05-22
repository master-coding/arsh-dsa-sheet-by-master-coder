## Sort Colors

```cpp
// time: O(nlogn)
class Solution {
public:
    void sortColors(vector<int>& nums) {
        sort(nums.begin(), nums.end());
    }
};
```

```cpp
// time: O(n), space: O(1)
// require two traversals 

class Solution {
public:
    void sortColors(vector<int>& nums) {
        int zeroes = 0, ones = 0;
        
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] == 0) zeroes++;
            else if (nums[i] == 1) ones++;
        }
        
        int twos = nums.size() - zeroes - ones;
        int index = 0;
        
        while (zeroes--) { nums[index] = 0; index++; }
        while (ones--) { nums[index] = 1; index++; }
        while (twos--) { nums[index] = 2; index++; }
    }
};
```

```cpp
// using Dutch National Flag alogrithm
// time: O(n), space: O(1)

class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, high = nums.size() - 1;
        int curr = 0;
        
        while (curr <= high) {
            if (nums[curr] == 0) {
                swap(nums[curr], nums[low]);
                low++;
                curr++;
            }
            else if (nums[curr] == 1) {
                curr++;
            }
            else {
                swap(nums[curr], nums[high]);
                high--;
            }
        }
        
    }
};
```

In this method the elements between  
[0, low) => 0  
[low, high] => 1  
[high + 1, n) => 2  
