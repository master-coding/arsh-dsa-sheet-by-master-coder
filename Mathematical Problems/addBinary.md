## Add Binary (Leetcode 67)

```cpp
class Solution {
public:
    string addBinary(string &a, string &b) {
        string res = "";
        
        if (a.length() < b.length())
            swap(a, b);
        int sizeDiff = a.length() - b.length();
        
        reverse(b.begin(), b.end());
        for (int i = 0; i < sizeDiff; i++) {
            b.push_back('0');
        }
        
        reverse(b.begin(), b.end());
        
        char carry = '0';
        for (int i = a.length() - 1; i >= 0; i--) {
            char first = a[i], second = b[i];
                       
            if (carry == '0') {
                if (first == '0' and second == '0') {
                    res.push_back('0');
                    carry = '0';
                }
                else if ((first == '0' and second == '1') or (first == '1' and second == '0')) {
                    res.push_back('1');
                    carry = '0';
                }
                else {
                    res.push_back('0');
                    carry = '1';
                }
            }
            else {
                if (first == '0' and second == '0') {
                    res.push_back('1');
                    carry = '0';
                }
                else if ((first == '0' and second == '1') or (first == '1' and second == '0')) {
                    res.push_back('0');
                    carry = '1';
                }
                else {
                    res.push_back('1');
                    carry = '1';
                }
            }  
            // cout << carry << ' ' << first << ' ' << second << '\n';
        }
        
        if (carry == '1') res.push_back('1');
        
        reverse(res.begin(), res.end());
        
        return res;
    }
};
```
