## Find Pair Given Difference

```cpp
// { Driver Code Starts
#include<bits/stdc++.h>
using namespace std; 


bool findPair(int arr[], int size, int n);

int main() {
    int t;
    cin>>t;
    while(t--)
    {
        int l,n;
        cin>>l>>n;
        int arr[l];
        for(int i=0;i<l;i++)
            cin>>arr[i];
        if(findPair(arr, l, n))
            cout<<1<<endl;
        else cout<<"-1"<<endl;
    }
    
  
    return 0;
}// } Driver Code Ends

bool findPair(int arr[], int n, int target) {
    sort(arr, arr + n);
    
    int first = 0, second = 1;
    while (first < n and second < n) {
        if (first != second and arr[second] - arr[first] == target)
            return true;
        else if (arr[second] - arr[first] < target)
            second++;
        else
            first++;
    }
    
    return false;
}
```
