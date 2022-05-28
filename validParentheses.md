## Valid Parentheses

``` cpp
// time complexity: O(|s|), space: O(|s|)

class Solution {
public:
    bool isValid(string s) {
        unordered_map <char, int> m = {{'(', 1}, {'[', 2}, {'{', 3},
                                       {')', -1}, {']', -2}, {'}', -3}};
        stack <char> st;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(' or (s[i] == '[') or s[i] == '{') {
                st.push(s[i]);
            }
            else {
                if (st.empty()) return false;
                else {
                    if (m[s[i]] + m[st.top()] == 0) st.pop();
                    else return false;
                }
            }
        }
        
        return st.empty() ? true: false;
    }
};

```

```cpp
// time complexity: O(|s|), space: O(|s|)

class Solution {
public:
    bool isValid(string s) {
        stack <char> st;
        
        for (const char &parenthesis: s) {
            if (parenthesis == '(') st.push(')');
            else if (parenthesis == '{') st.push('}');
            else if (parenthesis == '[') st.push(']');
            // else {
            //     if (st.empty() or parenthesis != st.top()) return false;
            //     st.pop();
            // }
            else if (st.empty() or parenthesis != st.top()) return false;
            else st.pop();
        }
        
        return st.empty();
    }
};
```
