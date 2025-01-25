# Arrays-
Array basic 
..
<br>
initialisation 
<br>
int a[];
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
