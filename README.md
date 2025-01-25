# Arrays-
Array basic 
..
initialisation 
int a[];


int age = 22;
int *ptr = &age;
ptr++;   //ptr=ptr+1 +1 will represe datatype addition which will equal to its bit

array is a pointer
int *ptr = &arr[0];
int *ptr = arr;

int aadhar[10];
int *ptr = &aadhar[0];
ptr++;

#include <stdio.h>

int main() {
    int aadhar[5];
    int *ptr = &aadhar[0]; // Pointer pointing to the first element of the array

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

0 index: 101
1 index: 102
2 index: 103
3 index: 104
4 index: 105

reverse an array 
n-i-1

#include <stdio.h>
#include <conio.h>
int main() {
    int n;
    printf("enter n (n>2");
    scanf("%d",&n);
    
    int fib[n];
    fib[0] = 0;
    printf("%d",fib[0]);
    fib[1] = 1;
    printf("%d",fib[1]);
    for(int i=2;i<n;i++){
        fib[i]=fib[i-1]+fib[i-2];
        printf("%d",fib[i]);
    }
    printf("\n");
    return 0;
}


