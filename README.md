# ARRAY

##### index
- [basic](#basic)
- [ADT](#ADT)
- [types](#Type)
- [size of an array](#size-of-an-array)
- [sparse matrix](#sparse-matrix)
- [striver a to z questions](#striver-a-to-z-questions)
  
# basic 
* elements aranged in continuous memory 
* elements are of same type 

## Array: Advantages & Disadvantages 

###  Advantages

*  **Fast access** using index (O(1))
*  **Simple to use & understand**
*  **Contiguous memory allocation**
*  **Efficient for fixed-size data**

###  Disadvantages

*  **Fixed size** (cannot grow/shrink easily)
*  **Memory wastage** if size is overestimated
*  **Insertion/Deletion is costly** (shifting needed)
*  **Not suitable for dynamic data**
  
---  
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

#### type 
---

## 🔷 Types of Arrays

#### 🔹 1. One-Dimensional Array (1D)
#### 🔹 2. Two-Dimensional Array (2D)
#### 🔹 3. Multi-Dimensional Array
#### 🔹 4. Static Array
#### 🔹 5. Dynamic Array
#### 🔹 6. Jagged Array
      * Array of arrays with **unequal sizes**
      * Supported using pointers / vectors
     
---
---

## size of an array
numbers of elements = (upper bound - lower buond) + 1 

#### indexing 
```
1 D 
arr[index] = base + ((index - lower bound)*weight)
a[i] = B +((i - LB)*W)

2 D 
row major address
       arr[i][j] = B + [N*(i - LR) + (j - LC)] x size 

column major address 
       arr[i][j] = B + [(i - LR) + M*(j - LC)] x size

arr[LR : UR][LC : UC] 
M = no. of rows
N = no. of coloumns 
LR AND LC are usualy 0 .

3 D
Row major 
Address(arr[i][j][k]) =  B + [ (i − LR) * (NC * ND) + (j − LC) * ND + (k − LD) ] x size 

NC = UC − LC + 1   // number of columns 
ND = UD − LD + 1   // number of depth 

column major
Address(arr[i][j][k]) = B + [ (k − LD) * (NR * NC) + (j − LC) * NR + (i − LR) ] x size 

NR = UR − LR + 1   // number of rows
NC = UC − LC + 1   // number of columns
```

---

## sparse matrix 
---
* A **sparse matrix** is a matrix in which **most of the elements are 0**.
* If a matrix of size **m × n** has **very few non-zero elements**, it is called a sparse matrix.

* **Condition**
* A matrix is sparse if:
* Number of zero elements  >  Number of non-zero elements

### Why use Sparse Matrix?

* **Storage Efficiency**
* Instead of storing all zeros, we store **only non-zero elements**.
* This reduces **memory usage**.

* **Faster Computation**
* Operations are performed only on **non-zero elements**, saving time.

---

### Example
Matrix (4 × 4):

```
0 0 3 0
0 0 0 8
1 0 3 0
0 0 7 0
```
---

* **Drawback of Normal 2D Array Representation**
* Storing sparse matrix in a 2D array wastes memory because **zeros occupy space but have no value**.

* **Sparse Matrix Representation**
* Instead of storing zeros, we store only **non-zero elements** using **triples**:

> A sparse matrix stores mostly zero values, so memory and computation can be optimized by storing only non-zero elements using special representations.


---

### striver a to z questions 
- [boiler plate code](#boiler-plate-code)
- [find largest element](#largest-element)
- [find second smallest largest ](#second-smallest-and-largest)
- [chech if array is sorted](#check-sort)
- [remove duplicate](#remove-duplicate)
- [left rotate array by one place](#left-rotate-array)
- [left rotate upto d index](#left-rotate-upto-d-index)
- [shift zeros to the last](#shift-zeros-to-the-last)
- [linear search](#linear-search)
- [union array of two sorted array](#union-array-of-two-sorted-array)
- [intersection of array](#intersection-of-array)
- [find missing number](#find-missing-number)
- [maximum no. of consecutive ones](#maximum-no-of-consecutive-ones)
- [find single number](#find-single-number)
- [longest subarray with sum k](#longest-subarray-with-sum-k)
- [two sum](#two-sum)
- [sort an aaray of zeros ones wos](#sort-an-aaray-of-zeros-ones-twos)
- [majority element n divide two](#majority-element-n-divide-two)
- [kadanes algorithm maximum subarray sum](#kadanes-algorithm-maximum-subarray-sum)

#### boiler plate code
```cpp
#include <bits/stdc++.h>
#include <vector>
using namespace std;

// Function to find largest element


// function for displaying array aftercalling function
void display(const vector<int>& v) {
    for (int x : v) {
        cout << x << " ";
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;

    vector<int> arr(n);
    cout << "Enter array elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // ---- Display array ----
    cout << "Array elements : ";
    for (int i = 0; i < n; i++) {
         cout << arr[i] << " ";
    }
    cout << endl;

    // ---- Function call ----
    vector<int> arrayanswer =  ; //function 
    int answer = 0;

    // ----- Display answer -----
    cout << "answer to this question is : " << answer << "\n";

    // ------ display function after call ------
    cout << "array after call : ";
    display(arrayanswer);

    return 0;
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


###### second smallest and largest 

```cpp
//BRUTE
//sort and check if from the back the element is equal to largest aka last element eg : 1 2 3 4 5 7 7  TC = O(NLOGN + N )

//BETTER
//check while traversing if the elem is largest than the largest aka 0 index and it  TC = O(2N)

int largestElement(vector<int> &arr, int n) {
int largest = arr[0];
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
    cout << endl;

return secondLargest;
}
```

```cpp
//OPTIMAL
#include <bits/stdc++.h>
using namespace std;

int secondLargest(vector<int> &arr, int n) {
    int largest = arr[0];
    int slargest = -1; // for all positives;
                // INT_MIN if array contains negatives

    for (int i = 1; i < n; i++) {
        if (arr[i] > largest) {
            slargest = largest;
            largest = arr[i];
        }
        else if (arr[i] < largest && arr[i] > slargest) {
            slargest = arr[i];
        }
    }

return slargest;

//TC = O(N)
}

int secondSmallest(vector<int> &arr, int n) {
    int smallest = arr[0];
    int ssmallest = INT_MAX;

    for (int i = 1; i < n; i++) {
        if (arr[i] < smallest) {
            ssmallest = smallest;
            smallest = arr[i];
        }
        else if (arr[i] != smallest && arr[i] < ssmallest) {
            ssmallest = arr[i];
        }
    }
    return ssmallest;
//TC = O(N)
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
bool check_sorted(const vector<int>& ar, int n) {
    for (int i = 1; i < n; i++) {
        if (ar[i] <= ar[i - 1]) {
            return false;   // stop immediately
        }
    }
    return true;
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
vector<int> rotateArray(vector<int>& arr, int n){
    int temp = arr[0] ;
    for (int i = 1; i<n; i++) {
        arr[i-1] = arr[i];
    }
    arr[n-1] = temp;

return arr;
}
```
###### left rotate upto d index
* TC = O(n+d)
* SC = O(d)
* **brute approach**

```cpp
vector<int> leftRotate(vector<int>& arr, int n) {
    cout << "how many shifting : ";
    int d;
    cin >> d;
    d = d % n;

    vector<int> temp(d);
    for (int i = 0; i < d; i++){
        temp [i] = arr[i]; // puting temprory elements 
    }
    for (int i = d; i < n; i++){
        arr[i - d] = arr[i]; //shifting
    }
    for (int i = n - d; i < n; i++){
        arr[i] = temp[i - (n-d)]; //pull back temp
    }

return arr;
}
```

---
* **optimal approach**
* TC = O(N)
* SC = O(1)


```cpp
vector<int> leftRotate(vector<int>& arr, int n) {
    cout << "how many shifting : ";
    int d;
    cin >> d;
    d = d % n;

    reverse(arr.begin(), arr.begin() + d);
    reverse(arr.begin() + d, arr.end());
    reverse(arr.begin(), arr.end());


return arr;
}
```
```cpp
void reverseVector(vector<int>& arr, int start, int end) {
    while (start < end) {   // < is better than <=
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}
```

### right rotate array upto d index
```cpp
vector<int> rightRotate(vector<int>& arr, int n) {
    cout << "how many shifting : ";
    int d;
    cin >> d;
    d = d % n;

    reverse(arr.begin(), arr.begin() + d + 1);
    reverse(arr.begin() + d + 1, arr.end());
    reverse(arr.begin(), arr.end());

return arr;
}
```

###### shift zeros to the last
* **brute force**
* TC = O(N)
* SC = O(N)

```cpp
vector<int> moveZeros(int n, vector<int>& arr) {
    // step 1: store non-zero elements
    vector<int> temp;
    for(int i = 0;i<n; i++) {
        if (arr[i] != 0){
            temp.push_back(arr[i]);
        }
    }
    // step 2: copy back non-zeros
    int nz = temp.size();
    for(int i = 0; i<nz; i++) {
        arr[i] = temp[i];
    }

    // step 3: fill remaining with zeros
    for(int i = nz; i<n; i++) {
        arr[i] =0;
    }  
return arr;
}
```
* **optimal approach**
* TC = O(N)
* SC = O(N)
```cpp
vector<int> moveZeros(int n, vector<int> arr) {
    int j = -1;
    for(int i = 0;i<n; i++) {
        if(arr[i] == 0) {
            j = i;
            break;
        }
    }
    // no non zero numbers
    if(j == -1) return arr;

    for(int i = j+1;i<n; i++) {
        if(arr[i] != 0) {
            swap(arr[i],arr[j]);
            j++;
        }
    }
return arr;
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
* for testing
```cpp
int linearSearch(vector<int>& arr, int n ) {
    cout << "enter no. to be found : ";
    int num ;
    cin >> num ;
    for (int i = 0; i < n; i++) {
        if (arr[i] == num) {
            return i; // found
        }
    }
    return -1; // not found
}
```


###### union array of two sorted array
```
TC = O(N1log n + N2log n) + O(N1+N2)
SC = O(N1+N2) +O(N1+N2)
```

```cpp
vector<int> sortedArray(vector<int>& arr,vector<int>& b) {
    int n1 = arr.size();
    int n2 = b.size();

    set<int> st;

    // insert elements of a
    for (int i = 0; i < n1; i++) {
        st.insert(arr[i]);
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
// this code can be used for unsorted array also as it is using set
```

---

* TC = O(N1 + N2)
* SC = O(N1 + N2) //not for the nswer but for the ans to return 

```cpp
vector < int > sortedArray(vector < int > a,vector < int > b) {
    int n1 = a.size();
    int n2 = b.size();
    int i = 0;
    int j = 0;
    vector<int> unionArr;
    while(i<n1 && j < n2) {
        if(a[i] <= b[j]) {
            if(unionArr.size() == 0 || unionArr.back() != a[i]) {
                unionArr.push_back(a[i]);
            }
            i++;
        }
        else {
            if(unionArr.size() == 0 || unionArr.back() != b[j]) {
                unionArr.push_back(b[j]);
            }
            j++;
        }
    }
    
    while(j<n2) {
        if(unionArr.size() == 0 || unionArr.back () != b[j]) {
            unionArr.push_back(b[j]);
        }
        j++;
    }

    while(i<n1) {
        if(unionArr.size() == 0 || unionArr.back() != a[i]) {
            unionArr.push_back(a[i]);
        }
        i++;
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
vector<int> findArrayIntersection(vector<int> &A, int n, vector<int> &B, int m) {
    vector<int> vis(m, 0); // mark visited in B
    
    vector<int> ans;
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
vector<int> findArrayIntersection(vector<int> &A, int n,vector<int> &B, int m) {

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
* **brute force**
* TC O(N*N)
* SC =O(1)

```cpp
int missingNumber(vector<int>& arr, int n) {
    for (int i = 1; i <= n; i++) {
        int flag = 0;
        for (int j = 0; j < n - 1; j++) {
            if (arr[j] == i) {
                flag = 1;
                break;
            }
        }
        if (flag == 0) return i;
    }
    return -1;
}
```
---

* **BETTER**
* TC = O(N)+O(N)
* SC = O(N)

```cpp
int missing_Number(vector<int>& arr,int n){
    int N = n;

    // Step 1: Create hash array of size N+1 initialized with 0
    vector<int> hashArr(n + 1, 0);

    // Step 2: Mark elements present in arr
    for (int i = 0; i < n-1; i++) {
        hashArr[arr[i]] = 1;
    }

    // Step 3: Find the index which is still 0 → that's the missing number
    int ans = 0;  
    for (int i = 1; i <= N; i++) {
        if (hashArr[i] == 0) {
            ans = i;
        }
    }

    return ans;
}
```
* **optimal**
* by sum method <br>
TC = O(N) <br>
SC = O(1)
```cpp
int missing_Number(vector<int>& arr,int n){
    int N = n + 1;
    // Step 1: Calculate expected sum of 1 to N
    int sum = N * (N + 1) / 2;

    // Step 2: Calculate actual sum of array
    int s2 = 0;
    for (int i = 0; i < n; i++) {
        s2 += arr[i];
    }

    // Step 3: Missing number = expected sum - actual sum
    int ans = (sum - s2);

    return ans ;
}
```
---
* by XOR <br>
TC = O(N) <br>
SC = O(1)

```cpp
int missing_Number(vector<int>& arr,int n){
    int N = n +1;

    int xor1 = 0;
    for (int i = 1; i <= N; i++) {
        xor1 ^= i;
    }

    int xor2 = 0;
    for (int i = 0; i < N - 1; i++) {
        xor2 ^= arr[i];
    }
    int ans = (xor1 ^ xor2);
    return ans;
}
```
###### maximum no. of consecutive ones
```cpp
int findMaxConsecutiveOnes(vector<int>& arr) {
    int maxi = 0;
    int cnt = 0;

    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == 1) {
            cnt++;
            maxi = max(maxi, cnt);
        } else {
            cnt = 0;
        }
    }

    return maxi;
}
```

###### find single number 
* brute force 
```cpp
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
```

* optimal
```cpp
int singleNumber(vector<int> &arr) {
    int xorr = 0;
    for (int i = 0; i < arr.size(); i++) {
        xorr = xorr ^ arr[i];
    }
    return xorr;
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

###### sort an aaray of zeros ones twos
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
###### majority element n divide two
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

### kadanes algorithm maximum subarray sum
```cpp
//brute aproach

TC = O(N³)    SC = O(1)

for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        int sum = 0;
        for (int k = i; k <= j; k++) {
            sum += arr[k];
        }
        maxm = max(maxm, sum);
    }
}

//better aproach 

TC = O(N²)    SC = O(1)

int maxm = INT_MIN;

for (int i = 0; i < n; i++) {
     int sum = 0;
    for (int j = i; j < n; j++) {
        int sum = sum + arr;
    }
}


// optimal - kadans algorithm

TC = O(N)    SC = O(1)

int sum = 0, maxm = INT_MIN;
int start = 0, ansStart = 0, ansEnd = 0;

for (int i = 0; i < n; i++) {
    if (sum == 0) start = i;

    sum += arr[i];

    if (sum > maxm) {
        maxm = sum;
        ansStart = start;
        ansEnd = i;
    }

    if (sum < 0) {
        sum = 0;
    }
}

```


