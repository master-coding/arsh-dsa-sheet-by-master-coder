## Valid Palindrome II

```cpp
class Solution {
public:
    bool isPalindrome(string &s, int start, int end) {
        while (start < end) {
            if (s[start] == s[end]) {
                start++;
                end--;
            }
            else
                return false;
        }
        
        return true;
    }
    
    bool validPalindrome(string s) {
        int left = 0, right = s.length() - 1;
        
        while (left < right) {
            if (s[left] == s[right]) {
                left++;
                right--;
            }
            else {
                return isPalindrome(s, left, right - 1) or isPalindrome(s, left + 1, right);          
            }
        }
        
        return true;
    }
};
```