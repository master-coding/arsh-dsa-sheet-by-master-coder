## Implement strStr()

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        if (needle.length() == 0) return 0; // needle length will not be 0 acc. to constraints
        
        for (int i = 0; i < haystack.length(); i++) {
            if (haystack[i] == needle[0]) {
                int hay = i, need = 0;
                
                while (need < needle.size() and hay < haystack.size()) {
                    if (haystack[hay] != needle[need])
                        break;
                    else {
                        need++;
                        hay++;
                    }
                }
                
                if (need == needle.size())
                    return i;
            }
        }
        
        return -1;
    }
};
```