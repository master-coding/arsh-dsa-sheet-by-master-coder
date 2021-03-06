## Backspace String Compare

```cpp
// time: O(|s|) + O(|t|)
// space: O(|s|) + O(|t|)

class Solution {
public:
    bool backspaceCompare(string s, string t) {        
        string first = "", second = "";
        
        for (const char &character: s) {
            if (character != '#') first.push_back(character);
            else {
                if (first.size() != 0) first.pop_back();
            }
        }
        
        for (const char &character: t) {
            if (character != '#') second.push_back(character);
            else {
                if (second.size() != 0) second.pop_back();
            }
        }
        
        return first == second;
    }
};
```

```cpp
// time: O(n), space: O(1)

class Solution {
public:
    bool backspaceCompare(string s, string t) {
        int i = s.length() - 1, j = t.length() - 1;
        int count1 = 0, count2 = 0;
        
        while (i >= 0 or j >= 0) {
            while (i >= 0 and (count1 > 0 or s[i] == '#')) {
                if (s[i] == '#') count1++;
                else count1--;
                
                i--;
            }
            
            while (j >= 0 and (count2 > 0 or t[j] == '#')) {
                if (t[j] == '#') count2++;
                else count2--;
                
                j--;
            }
            
            if (i >= 0 and j >= 0 and s[i] == t[j]) {
                i--;
                j--;
            }
            else {
                return i == -1 and j == -1;
            }
        }
        
        return true;
    }
};

```
