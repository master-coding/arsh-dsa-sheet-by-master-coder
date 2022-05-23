## Backspace String Compare

```cpp
// time: O(|s|) + O(|t|)

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
