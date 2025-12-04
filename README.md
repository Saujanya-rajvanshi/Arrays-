# Arrays

##### index
1. insertion ,del ,search,rev ,display
2. find largest element
3. second largest
4. remove duplication
5. left rotate one place
6. left rotate upto d place

###### ins , del , search , rev , dis
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

###### largest elem
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
```


Array basic 
```cpp
#include <bits/stdc++.h>
using namespace std;

int secondLargest(vector<int> &a, int n) {
    int largest = a[0];
    int slargest = -1;

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

