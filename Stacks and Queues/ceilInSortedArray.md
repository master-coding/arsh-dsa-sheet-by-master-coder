## Ceiling in a sorted array

```cpp
// time complexity: O(n)
#include <iostream>
using namespace std;


int ceilOfX(int arr[], int n, int x) {
    if (x <= arr[0]) return arr[0];
    if (x > arr[n - 1]) return -1;
    if (x == arr[n - 1]) return arr[n - 1];

    int i = 0;
    while (arr[i] < x) 
        i++;

    return arr[i];
}

int main() {
    cout << "Enter the size of the array: ";
    int n; cin >> n;
    cout << "Enter the elements of the array: ";
    int arr[n];
    for (int i = 0; i < n; i++) cin >> arr[i];

    cout << "Enter the element: ";
    int x; cin >> x;

    cout << "ceil of x is : " << ceilOfX(arr, n, x);
}

```

```cpp
// time complexity: O(logn)
#include <iostream>
using namespace std;


int helper(int arr[], int low, int high, int x) {
    if (x <= arr[low]) return low;
    if (x > arr[high]) return -1;

    int mid = low + (high - low) / 2;

    if (arr[mid] == x) return mid;

    else if (arr[mid] < x) {
        // if (mid + 1 <= high and x <= arr[mid + 1])
        //     return mid + 1;
        return helper(arr, mid + 1, high, x);
    }
    else {
        // if (mid - 1 >= low and x > arr[mid - 1])
        //     return mid;

        return helper(arr, low, mid, x);
    }
}

int ceilOfX(int arr[], int n, int x) {
    int ans = helper(arr, 0, n - 1, x);

    if (ans == -1) return -1;
    
    return arr[ans];
}

int main() {
    cout << "Enter the size of the array: ";
    int n; cin >> n;
    cout << "Enter the elements of the array: ";
    int arr[n];
    for (int i = 0; i < n; i++) cin >> arr[i];

    cout << "Enter the element: ";
    int x; cin >> x;

    cout << "ceil of x is : " << ceilOfX(arr, n, x);
}
```

```cpp
// time complexity: O(logn)
#include <iostream>
using namespace std;


int ceilOfX(int arr[], int n, int x) {
    if (x <= arr[0]) return arr[0];
    if (x > arr[n - 1]) return -1;

    int low = 0, high = n - 1;    

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] == x) return arr[mid];
        if (arr[mid] < x) low = mid + 1;
        else high = mid - 1;
    }
    return arr[low];
}

int main() {
    cout << "Enter the size of the array: ";
    int n; cin >> n;
    cout << "Enter the elements of the array: ";
    int arr[n];
    for (int i = 0; i < n; i++) cin >> arr[i];

    cout << "Enter the element: ";
    int x; cin >> x;

    cout << "ceil of x is : " << ceilOfX(arr, n, x);
}
```
