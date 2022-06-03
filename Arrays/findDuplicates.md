## Find All Duplicates in an Array (leetcode 442)

```cpp
// time complexity: O(n**2)
// it wil give TLE

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector <int> res;
        for (int i = 0; i < nums.size() - 1; i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[j] == nums[i]) {
                    res.push_back(nums[i]);
                    break;
                }
            }
        }
        
        
        return res;
    }
};
```

```cpp
// time complexity: O(nlogn)

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector <int> res;
        
        sort(nums.begin(), nums.end());
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] == nums[i - 1])
                res.push_back(nums[i]);
        }

        return res;
    }
};
```

```cpp
// time complexity: O(n), auxillary space: O(n)

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector <int> res;

        unordered_map <int, int> m;
        for (int i = 0; i < nums.size(); i++)
            m[nums[i]]++;
        
        for (const auto &freq: m) {
            if (freq.second == 2)
                res.push_back(freq.first);
        }

        return res;
    }
};
```

```cpp
// time complexity: O(n)
// but it modifies the array

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector <int> res;

        for (int i = 0; i < nums.size(); i++) {
            int elementAtIndex = nums[abs(nums[i]) - 1];
            if (elementAtIndex < 0) {
                res.push_back( abs(nums[i]) );
            }
            else {
                nums[abs(nums[i]) - 1] *= -1;
            }
        }

        return res;
    }
};
```

```cpp
// time complexity: O(N)
// a slightly complex solution

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector <int> res;

        int n = nums.size();
        for (int i = 0; i < n; i++) {
            nums[(nums[i] - 1) % n] += n;
        }
        
        for (int i = 0; i < n; i++) {
        // arr[i] / n is greater than 2. 
        // Which guarantees that the number n has been added to that index
            if (nums[i] > 2*n)
                res.push_back(i + 1);
        }

        return res;
    }
};
```
