# ARRAY

##### index
- [ADT](#ADT)
- [find largest element](#largest-element)
- [find second largest](#second-largest)
- [chech if array is sorted](#check-sort)
- [remove duplicate](#remove-duplicate)
- [left rotate array](#left-rotate-array)
6. left rotate upto d place
7. shift zeros to the last
8. linear search
9. union of array
10. intersection of array
11. find the missing number
12. maximum no. of consecutive ones
13. longest subarray with sum k
14. two sum
15. sort an aaray of 0`s 1`s & 2`s
16. majaority element n/2
    
###### ADT
```cpp
#include <iostream>
using namespace std;

#define MAX 5

void insertElement(int *ar, int p, int n);
void display(int *ar);
void reverseArray(int *ar);
void deleteElement(int *ar, int p);
void searchElement(int *ar, int n);

int main() {
    int ar[MAX] = {0};

    insertElement(ar, 0, 11);
    insertElement(ar, 1, 12);
    insertElement(ar, 2, 13);
    insertElement(ar, 3, 14);
    insertElement(ar, 4, 15);

    cout << "Array after insertion:\n";
    display(ar);

    cout << "\nArray after deletion (delete position 2):\n";
    deleteElement(ar, 2);
    display(ar);

    insertElement(ar, 2, 13);

    cout << "\nArray after reverse:\n";
    reverseArray(ar);
    display(ar);

    int n;
    cout << "\nWhich element do you want to search? ";
    cin >> n;
    searchElement(ar, n);

    return 0;
}

void insertElement(int *ar, int p, int n) {
    if (p < 0 || p >= MAX) {
        cout << "Invalid position!\n";
        return;
    }
    for (int i = MAX - 1; i > p; i--) {
        ar[i] = ar[i - 1];
    }
    ar[p] = n;
}

void deleteElement(int *ar, int p) {
    if (p < 0 || p >= MAX) {
        cout << "Invalid position!\n";
        return;
    }
    for (int i = p; i < MAX - 1; i++) {
        ar[i] = ar[i + 1];
    }
    ar[MAX - 1] = 0;
}

void reverseArray(int *ar) {
    for (int i = 0; i < MAX / 2; i++) {
        int t = ar[i];
        ar[i] = ar[MAX - 1 - i];
        ar[MAX - 1 - i] = t;
    }
}

void searchElement(int *ar, int n) {
    for (int i = 0; i < MAX; i++) {
        if (ar[i] == n) {
            cout << "Element " << n << " found at position " << i + 1 << endl;
            return;
        }
    }
    cout << "Element " << n << " not found.\n";
}

void display(int *ar) {
    for (int i = 0; i < MAX; i++) {
        cout << ar[i] << " ";
    }
    cout << endl;
}
```

###### largest element
```cpp
#include <bits/stdc++.h>
largestElement(vector<int> &arr, int n) {
    int largest = arr[0] ;
    for(int i = 0;i<n; i++) {
        if(arr[i] > largest) {
            largest = arr[i];
        }
    }
return largest;
}

//TC = O(N)
```


###### second largest 

```cpp
//BRUTE
//sort and check if from the back the element is equal to largest aka last element eg : 1 2 3 4 5 7 7  TC = O(NLOGN + N )

//BETTER
//check while traversing if the elem is largest than the largest aka 0 index and it  TC = O(2N)

    int largest = ar[0];
    int secondLargest = -1;

    for (int i = 0; i < n; i++) {
        if (arr[i] > largest) {
            largest = arr[i];
        }
    }
    for (int i = 0; i < n; i++) {
        if (arr[i] > secondLargest && arr[i] != largest) {
            secondLargest = arr[i];
        }
    }

    cout << "Second Largest: " << secondLargest;
```

```cpp
//OPTIMAL
#include <bits/stdc++.h>
using namespace std;

int secondLargest(vector<int> &a, int n) {
    int largest = a[0];
    int slargest = -1 // for all positives;
                // INT_MIN if array contains negatives

    for (int i = 1; i < n; i++) {
        if (a[i] > largest) {
            slargest = largest;
            largest = a[i];
        }
        else if (a[i] < largest && a[i] > slargest) {
            slargest = a[i];
        }
    }

    return slargest;

//TC = O(N)
}

int secondSmallest(vector<int> &a, int n) {
    int smallest = a[0];
    int ssmallest = INT_MAX;

    for (int i = 1; i < n; i++) {
        if (a[i] < smallest) {
            ssmallest = smallest;
            smallest = a[i];
        }
        else if (a[i] != smallest && a[i] < ssmallest) {
            ssmallest = a[i];
        }
    }

    return ssmallest;
}

int main() {
    vector<int> a = {5, 1, 9, 3, 7};
    int n = a.size();

    cout << "Second Largest: " << secondLargest(a, n) << endl;
    cout << "Second Smallest: " << secondSmallest(a, n) << endl;

    return 0;
}
```
###### check sort 
```cpp
for(i=0;i<n;i++){
    if (ar[i] >= ar[i-1]{
        cout << "array is sorted "
    }
    else{
        cout << "array is not sorted";
}
```

###### remove duplicate
```cpp
int removeDuplicates(vector<int> &arr, int n) {
    int i = 0;
    for(int j = 1; j<n; j++) {
        if(arr[i] != arr[j]) {
            arr[i+1] = arr[j];
            i++:
       }
}
return i+1;
}
```

###### left rotate array
```cpp
#include <bits/stdc++.h>
vector<int> rotateArray(vector<int> &arr, int temp,i){
    int temp = arr[0] ;
    for (int i = 1; i<n; i++) {
        arr[i-1] = arr[i];
    }
    arr[n-1] = temp;
    return arr;
}
```
###### left rotate upto d index
       TC = O(n+d)
       SC = O(d)
```cpp
#include <bits/stdc++.h>
#include <iostream>
using namespace std;
void leftRotate(int arr[], int n, int d) {
    d = d % n;

    int temp [d];
    for (int i = 0; i < d; i++){
        temp [i] = arr[i];
    }
    for (int i = d; i < n; i++){
        arr[i - d] = arr[i];
    }
    for (int i = n - d; i < n; i++){
        arr[i] = temp[i - (n-d)];
}
```

```
TC = O(N)
SC = O(1)
```
```cpp
#include <bits/stdc++.h>
#include <iostream>
using namespace std;
void leftRotate(int arr[], int n, int d){
    reverse(arr, arr+d);
    reverse(arr+d, arr+n) ;
    reverse(arr, arr+n);

int main() {
    int n;
    cin >> n;
    int arr[n];
    for(int i = 0; i<n; i++) {
        cin >> arr[i];
    }
    int d;
    cin >> d;
    leftRotate(arr, n, d);
    for(int i = 0;i<n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```
```cpp
void Reverse(int arr[], int start, int end){
    while (start <= end){
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end --;
    }
}
```

###### shift zeros to the last
```cpp
vector<int> moveZeros(int n, vector<int> a) {

// step - 1
vector<int> temp;
for(int i = 0;i<n; i++) {
    if(a[i] != ø) {
        temp.push_back(a[i]);
}
// step - 2
int nz = temp.size();
for(int i = 0; i<nz; i++) {
     a[i] = temp[i];
}
// step - 3
for(int i = nz; i<n; i++) {
    a[i] =0;
}
}
```
```cpp
vector<int> moveZeros(int n, vector<int> a) {
    int j = -1;
    for(int i = 0;i<n; i++) {
        if(a[i] == 0) {
            j = i;
            break;
        }
    }

// no non zero numbers
if(j == -1) return a;

for(int i = j+1;i<n; i++) {
    if(a[i] != 0) {
        swap (a[i],a[j]);
        j++;
    }
}
```

###### linear search
```cpp
int linearSearch(int n, int num, vector<int> &arr) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == num) {
            return i; // found
        }
    }
    return -1; // not found
}
```
###### union array
```
TC = O(N1log n + N2log n) + O(N1+N2)
SC = O(N1+N2) +O(N1+N2)
```

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> sortedArray(vector<int> a, vector<int> b) {

    int n1 = a.size();
    int n2 = b.size();

    set<int> st;

    // insert elements of a
    for (int i = 0; i < n1; i++) {
        st.insert(a[i]);
    }

    // insert elements of b
    for (int i = 0; i < n2; i++) {
        st.insert(b[i]);
    }

    // copy set to vector
    vector<int> temp;
    for (auto it : st) {
        temp.push_back(it);
    }

    return temp;
}
```
```
TC = O(N1 + N2)
SC = O(N1 + N2) //not for the nswer but for the ans to return 
```
```cpp
#include<bits/stdc++.h>
vector < int > sortedArray(vector < int > a,
vector < int > b) {
    int n1 = a.size();
    int n2 = b.size();
    int i = 0;
    int j = 0;
vector<int> unionArr;
while(i<n1 && j < n2) {
    if(a[i] <= b[j]) {
        if(unionArr.size() == 0 | | unionArr.back() != a[i]) {
            unionArr.push_back(a[i]);
       }
       i++;
    }
    else {
        if(unionArr.size() == 0 | | unionArr.back() != b[j]) {
            unionArr.push_back(b[j]);
        }
        j++;
    }
}

while(j<n2) {
    if(unionArr.size() == 0 | | unionArr.back () != b[j]) {
        unionArr.push_back(b[j]);
    }
    j++;
}

while(i<n1) {
    if(unionArr.size() == 0 | | unionArr.back() != a[i]) {
        unionArr.push_back(a[i]);
    }
    i++:
}

return unionArr;
}
```

###### intersection of array
```
TC = O(N1 * N2)
SC = O(N2) 
```
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> findArrayIntersection(vector<int> &A, int n,
                                  vector<int> &B, int m) {

    vector<int> ans;
    int vis[m] = {0};  // mark visited in B

    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {

            if(A[i] == B[j] && vis[j] == 0) {
                ans.push_back(A[i]);
                vis[j] = 1;
                break;
            }

            if(B[j] > A[i]) break; 
        }
    }

    return ans;
}
```
```
TC = O(N1 + N2)
SC = O(1) 
```
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> findArrayIntersection(vector<int> &A, int n,
                                  vector<int> &B, int m) {

    int i = 0;
    int j = 0;
    vector<int> ans;

    while(i < n && j < m) {

        if(A[i] < B[j]) {
            i++;
        }
        else if(B[j] < A[i]) {
            j++;
        }
        else {
            ans.push_back(A[i]);
            i++;
            j++;
        }
    }

    return ans;
}
```
###### find missing number
```
TC = O(N)+O(N)
SC = O(N)
```
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int arr[] = {1, 2, 4, 5};
    int N = 5;   // numbers are from 1 to N
    int n = sizeof(arr) / sizeof(arr[0]);

    // Step 1: Create hash array of size N+1 initialized with 0
    vector<int> hashArr(N + 1, 0);

    // Step 2: Mark elements present in arr
    for (int i = 0; i < n-1; i++) {
        hashArr[arr[i]] = 1;
    }

    // Step 3: Find the index which is still 0 → that's the missing number
    for (int i = 1; i <= N; i++) {
        if (hashArr[i] == 0) {
            cout << "Missing number = " << i;
            return 0;
        }
    }

    return 0;
}
```
```
TC = O(N)
SC = O(1)
```
```cpp
//optimal aproach by sumation
#include <bits/stdc++.h>
using namespace std;

int main() {
    int arr[] = {1, 2, 3 ,4 ,5 ,6 ,8 ,9 ,10};
    int N = 10;  // numbers should be from 1 to N

    int n = sizeof(arr) / sizeof(arr[0]);

    // Step 1: Calculate expected sum of 1 to N
    int sum = N * (N + 1) / 2;

    // Step 2: Calculate actual sum of array
    int s2 = 0;
    for (int i = 0; i < n; i++) {
        s2 += arr[i];
    }

    // Step 3: Missing number = expected sum - actual sum
    cout << "Missing number = " << (sum - s2);

    return 0;
}
```
```
TC = O(N)
SC = O(1)
```
```cpp
//optimal aproach by xor
#include <bits/stdc++.h>
using namespace std;

int main() {
    int arr[] = {1, 2, 4, 5};
    int N = 5;

    int xor1 = 0;
    for (int i = 1; i <= N; i++) {
        xor1 ^= i;
    }

    int xor2 = 0;
    for (int i = 0; i < N - 1; i++) {
        xor2 ^= arr[i];
    }

    cout << "Missing number = " << (xor1 ^ xor2);
    return 0;
}
```
###### maximum no. of consecutive ones
```cpp
#include <bits/stdc++.h>
using namespace std;

int findMaxConsecutiveOnes(vector<int>& nums) {
    int maxi = 0;
    int cnt = 0;

    for (int i = 0; i < nums.size(); i++) {
        if (nums[i] == 1) {
            cnt++;
            maxi = max(maxi, cnt);
        } else {
            cnt = 0;
        }
    }

    return maxi;
}

int main() {
    vector<int> nums = {1, 1, 0, 1, 1, 1};

    cout << "Max consecutive ones = " << findMaxConsecutiveOnes(nums);

    return 0;
}
```
###### find single number 
```cpp
#include <bits/stdc++.h>
using namespace std;

int singleNumber(vector<int>& arr) {
    int n = arr.size();

    for (int i = 0; i < n; i++) {

        int num = arr[i];
        int cnt = 0;

        // Count frequency of arr[i]
        for (int j = 0; j < n; j++) {
            if (arr[j] == num) {
                cnt++;
            }
        }

        // If frequency is 1, this is the unique number
        if (cnt == 1) {
            return num;
        }
    }

    return -1; // Not found (optional)
}

int main() {
    vector<int> arr = {1, 2, 3, 2, 1};

    cout << singleNumber(arr);

    return 0;
}
```
```cpp
//optimal solution
#include <iostream>
#include <vector>
using namespace std;

int getSingleElement(vector<int> &arr) {
    int xorr = 0;
    for (int i = 0; i < arr.size(); i++) {
        xorr = xorr ^ arr[i];
    }
    return xorr;
}

int main() {
    vector<int> arr = {2,6,1,3,4,5,7,8,9};

    cout << getSingleElement(arr) << endl;

    return 0;
}
```
###### longest subarray with sum k
```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayWithSumK(vector<int> &a, long long k) {

    map<long long, int> preSumMap;
    long long sum = 0;
    int maxLen = 0;

    for(int i = 0; i < a.size(); i++) {

        sum += a[i];

        // Case 1: entire subarray from 0...i has sum k
        if (sum == k) {
            maxLen = max(maxLen, i + 1);
        }

        // Case 2: check if (sum - k) exists in map
        long long rem = sum - k;
        if (preSumMap.find(rem) != preSumMap.end()) {
            int len = i - preSumMap[rem];
            maxLen = max(maxLen, len);
        }

        // Store prefix sum if seeing for first time
        if (preSumMap.find(sum) == preSumMap.end()) {
            preSumMap[sum] = i;
        }
    }

    return maxLen;
}
```
```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayWithSumK(vector<int> &a, long long k) {

    int left = 0, right = 0;
    long long sum = 0;
    int maxLen = 0;
    int n = a.size();

    while (right < n) {

        sum += a[right];   // expand window

        // shrink window if sum is too big
        while (left <= right && sum > k) {
            sum -= a[left];
            left++;
        }

        // check if we got exactly k
        if (sum == k) {
            maxLen = max(maxLen, right - left + 1);
        }

        right++; // move right forward
    }

    return maxLen;
}
```
###### two sum
```cpp
string read(int n, vector<int> &book, int target) {
    map<int, int> mpp;

    for(int i = 0; i < n; i++) {
        int a = book[i];
        int more = target - a;

        // Check if the pair exists
        if(mpp.find(more) != mpp.end()) {
            return "YES";      // pair found
            // return {mpp[more], i}; // if you want indexes
        }

        // store current number's index
        mpp[a] = i;
    }

    return "NO";  // no pair found
}

```

```cpp
string read(int n, vector<int> book, int target) {

    int left = 0, right = n - 1;
    sort(book.begin(), book.end());

    while(left < right) {
        int sum = book[left] + book[right];

        if(sum == target) {
            return "YES";
        }
        else if(sum < target) {
            left++;
        }
        else {
            right--;
        }
    }

    return "NO";
}
```

###### sort an aaray of 0`s 1`s & 2`s
algorithm
```cpp
#include <bits/stdc++.h>
using namespace std;

void sortArray(vector<int>& arr, int n) {
    int low = 0, mid = 0, high = n - 1;

    while (mid <= high) {
        if (arr[mid] == 0) {
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        }
        else if (arr[mid] == 1) {
            mid++;
        }
        else { // arr[mid] == 2
            swap(arr[mid], arr[high]);
            high--;
        }
    }
}
```
###### majority element n/2
algorithm
```cpp
#include <bits/stdc++.h>
using namespace std;

int majorityElement(vector<int>& v) {
    unordered_map<int, int> mpp;

    for (int i = 0; i < v.size(); i++) {
        mpp[v[i]]++;
    }

    for (auto it : mpp) {
        if (it.second > v.size() / 2) {
            return it.first;
        }
    }

    return -1;
}
```
```cpp
#include <bits/stdc++.h>
using namespace std;

int majorityElement(vector<int>& v) {
    int cnt = 0;
    int el = -1;

    // Step 1: Find candidate
    for (int i = 0; i < v.size(); i++) {
        if (cnt == 0) {
            el = v[i];
            cnt = 1;
        } else if (v[i] == el) {
            cnt++;
        } else {
            cnt--;
        }
    }

    // Step 2: Verify candidate
    int cnt1 = 0;
    for (int i = 0; i < v.size(); i++) {
        if (v[i] == el) cnt1++;
    }

    if (cnt1 > v.size() / 2)
        return el;

    return -1;
}
```




