## Print all the duplicates in the input string

---

### Method 1
```cpp
// time complexity: O(n**2), space: O(128) => const

#include <iostream>
#include <vector>
using namespace std;


vector <pair<char, int>> printDuplicatesFreq(string s) {
    vector <pair<char, int>> res;
    bool isVisited[128] = {false};

    for (int i = 0; i < s.length(); i++) {
        int count = 1;
        if ( !isVisited[s[i]] ) {
            for (int j = i + 1; j < s.length(); j++) {
                if (s[j] == s[i]) count++;
            }    
        }
        
        isVisited[s[i]] = true;
        if (count > 1) res.push_back({s[i], count});
    }

    return res;
}

void printVectorOfPairs(vector<pair<char, int>> &v) {
    for (int i = 0; i < v.size(); i++) {
        cout << v[i].first << ' ' << " frequency: " << v[i].second << '\n';
    }
}

int main() {
    string s; getline(cin, s);
    vector <pair<char, int>> ans = printDuplicatesFreq(s);
    printVectorOfPairs(ans);
}

```

### Method 2
```cpp
// time complexity: O(n), space: O(128) => const
// Using count Array

#include <iostream>
#include <vector>
using namespace std;


vector <pair<char, int>> printDuplicatesFreq(string s) {
    int count[128] = {0};

    for (int i = 0; i < s.length(); i++) {
        count[s[i]]++;
    }

    vector <pair<char, int>> res;
    for (int i = 0; i < 128; i++) {
        if (count[i] > 1)
            res.push_back({(char)i, count[i]});
    }

    return res;
}

void printVectorOfPairs(vector<pair<char, int>> &v) {
    for (int i = 0; i < v.size(); i++) {
        cout << v[i].first << ' ' << " frequency: " << v[i].second << '\n';
    }
}

int main() {
    string s; getline(cin, s);
    vector <pair<char, int>> ans = printDuplicatesFreq(s);
    printVectorOfPairs(ans);

}

```

### Method 3
```cpp
// time complexity: O(n), space: O(different characters) => const
// Using unordered map

#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;


vector <pair<char, int>> printDuplicatesFreq(string s) {
    unordered_map <char, int> m;

    for (int i = 0; i < s.length(); i++) {
        m[s[i]]++;
    }

    vector <pair<char, int>> res;
    for (const auto &freq : m) {
        if (freq.second > 1)
            res.push_back({ freq.first, freq.second });
    }

    return res;
}

void printVectorOfPairs(vector<pair<char, int>> &v) {
    for (int i = 0; i < v.size(); i++) {
        cout << v[i].first << ' ' << " frequency: " << v[i].second << '\n';
    }
}

int main() {
    string s; getline(cin, s);
    vector <pair<char, int>> ans = printDuplicatesFreq(s);
    printVectorOfPairs(ans);
}
```
