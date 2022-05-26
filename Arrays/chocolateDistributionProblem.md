## Chocolate Distribution Problem

```cpp
// time complexity: O(nlogn)

#include <bits/stdc++.h>
using namespace std;

class Solution{
public:
    long long findMinDiff(vector<long long> a, long long n, long long m){
        sort(a.begin(), a.end());

        long long ans = a[m - 1] - a[0];
        for (int i = m; i < n; i++) {
            ans = min(ans, a[i] - a[i - m + 1]);
        }

        return ans;
    }
};

int main() {
	long long t; cin >> t;
	while(t--) {
		long long n; cin >> n;
		vector <long long> a;
		long long x;
		for(long long i = 0;i < n; i++) {
			cin >> x;
			a.push_back(x);
		}

		long long m; cin >> m;
		Solution ob;
		cout << ob.findMinDiff(a, n, m) << endl;
	}

	return 0;
}
```