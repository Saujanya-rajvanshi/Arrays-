# Arrays

##### index
1. insertion ,del ,search,rev ,display

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



```c
 #include <stdio.h>
 #define MAX100
 void display(int arr[], int n)
 {
 printf("Array elements: ");
 for (int i = 0; i < n; i++)
 printf("%d ", arr[i]);
 printf("\n");
 }
 void insert(int arr[], int *n, int pos, int val)
 {
 if (*n >= MAX) {
 printf("Array is full, insertion not possible!\n");
 return;
 }
 if (pos < 0 || pos > *n)
 {
 printf("Invalid position!\n");
 return;
 }
 for (int i = *n; i > pos; i--)
 arr[i] = arr[i- 1];
 arr[pos] = val;
 (*n)++;
 }
 void delete(int arr[], int *n, int pos) {
 if (*n <= 0) {
 printf("Array is empty, deletion not possible!\n");
 return;
 }
 if (pos < 0 || pos >= *n)
 {
 printf("Invalid position!\n");
 return;
 }
 for (int i = pos; i < *n- 1; i++)
 arr[i] = arr[i + 1];
 (*n)--;
 }
 void reverse(int arr[], int n)
 {
 int start = 0, end = n- 1
```











--- 
<br>
initialisation 
<br>
int a[ ];
<br>


int age = 22;
<br>
int *ptr = &age;<br>
ptr++;   //ptr=ptr+1 +1 will represe datatype addition which will equal to its bit<br>

array is a pointer<br>
int *ptr = &arr[0];<br>
int *ptr = arr;<br>

int aadhar[10];<br>
int *ptr = &aadhar[0];<br>
ptr++;<br>

#include <stdio.h><br>

int main() {<br>
    int aadhar[5];<br>
    int *ptr = &aadhar[0]; // Pointer pointing to the first element of the array<br>

    // Input loop
    for (int i = 0; i < 5; i++) {
        printf("%d index: ", i);
        scanf("%d", &aadhar[i]);
    }

    // Output loop
    for (int i = 0; i < 5; i++) {
        printf("%d index = %d\n", i, aadhar[i]);
    }

    return 0;
}
<br>
0 index: 101<br>
1 index: 102<br>
2 index: 103<br>
3 index: 104<br>
4 index: 105<br>

reverse an array <br>
n-i-1<br>

Your code is almost correct for generating and printing the Fibonacci series, but there are minor issues. Here's the corrected version of your program:

### Corrected Code:
```c
#include <stdio.h>

int main() {
    int n;
    printf("Enter n (n > 2): ");
    scanf("%d", &n);

    if (n <= 2) {
        printf("Please enter a value greater than 2.\n");
        return 1;
    }

    int fib[n];
    fib[0] = 0;
    printf("%d ", fib[0]);
    fib[1] = 1;
    printf("%d ", fib[1]);

    for (int i = 2; i < n; i++) {
        fib[i] = fib[i - 1] + fib[i - 2];
        printf("%d ", fib[i]);
    }

    printf("\n");
    return 0;
}
```

### Key Fixes:
1. **Added Validation for `n`:** Included a check to ensure the user enters a value greater than 2.
2. **Formatting in `printf`:** Added spaces after each number in the Fibonacci sequence for better readability.
3. **Removed `<conio.h>`:** `<conio.h>` is not required for this program and is non-standard.

### Example Output:
If the user enters `n = 10`, the program will output:

The provided code snippet appears to have some formatting and structural issues. Below is the corrected and properly formatted version of the program. The program is designed to store multiplication tables in a 2D array and print them.

### Corrected Code:
```c
#include <stdio.h>

// Function to store the multiplication table in a 2D array
void storeTable(int arr[][10], int n, int m, int number) {
    for (int i = 0; i < m; i++) {
        arr[n][i] = number * (i + 1);
    }
}

int main() {
    int tables[2][10];

    // Store tables of 2 and 3
    storeTable(tables, 0, 10, 2);
    storeTable(tables, 1, 10, 3);

    // Print the table of 2
    for (int i = 0; i < 10; i++) {
        printf("%d\t", tables[0][i]);
    }
    printf("\n");

    // Print the table of 3
    for (int i = 0; i < 10; i++) {
        printf("%d\t", tables[1][i]);
    }
    printf("\n");

    return 0;
}
```

### Explanation of Fixes:
1. **Proper Placement of `void storeTable` Function:** 
   - The `storeTable` function must be defined before its usage in `main`, or its prototype should be declared at the top.

2. **Fixed Formatting Issues:** 
   - Proper indentation and structured formatting for better readability.

3. **Corrected Loop Logic:** 
   - Ensured the `for` loop iterates correctly for the desired range (0 to `m-1`).

4. **Included Necessary Headers:**
   - Added `<stdio.h>` for standard input-output functions.

5. **Consistent Syntax:**
   - Ensured proper use of curly braces and semicolons.

### Output:
For this program, the output will be:

```
2	4	6	8	10	12	14	16	18	20	
3	6	9	12	15	18	21	24	27	30
```
```
Enter n (n > 2): 10
0 1 1 2 3 5 8 13 21 34
```
