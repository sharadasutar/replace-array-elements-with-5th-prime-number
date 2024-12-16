# replace-array-elements-with-5th-prime-number
Take 2D array int a[m][n], write a function to replace each element of the array with the 5th prime number starting from the corresponding array element in c

/*
   Name:SHARADA SUTAR
   Date:
   Description:Question2-Take 2D array int a[m][n], write a function to replace each element of the array with the 5th prime number starting from the corresponding array element in c
   Sample Input:
   Sample Output:

*/

#include <stdio.h>
#include <stdbool.h>

//#define M 3
//#define N 3

//Function to check if a number is prime 
bool isPrime(int num) 
{
    if(num < 2)              //condition to check if the number is not prime number
        return false;
    for(int i=2; i*i <=num; i++)
    {
        if(num % i == 0)            //condition if number is not prime i.e number modulus division gives 0 and if it gives non zero value that means its prime number 
            return false;
    }
    return true;
}


//Function to find the 5th prime number starting from a given number
int find5thPrime(int start)
{
    int count = 0;                       //initialize counter variable 
    int current = start;                
    while (count < 5)                      //condition for count upto 5 i.e upto 5th prime number
    {
        current++;                        //increment counter
        if(isPrime(current))               //check condition for prime number 
        {
            count++;                     //increment prime number
        }
    }
    return current;           
}

//Function to replace each element in the 2d array
void replaceWith5thPrime(int m, int n, int a[m][n])             //function to replace array element with prime number
{
    for(int i = 0; i< m; i++)                        //Run outer loop for rows

    {
        for(int j = 0; j < n; j++)                   //Run inner loop for columns
        {
            a[i][j] = find5thPrime(a[i][j]);             //store 5th prime number into array
        }
    }
}


//Function to print the array
void printArray(int m, int n, int a[m][n])
{
    for(int i = 0; i<m; i++)               //Run loop for rows
    {
        for(int j = 0; j < n; j++)           //Run loop for columns
        {
            printf("%d ",a[i][j]);           //print new array
        }
        printf("\n");
    }
}

//main function
int main()
{
    int m, n;

    //Get the dimensions of the array
    printf("Enter the number of rows: ");              //access input as number of rows through user 
    scanf("%d", &m);

    printf("Enter the number of columns: ");             //access input as number of columns through user 
    scanf("%d", &n);

    int a[m][n];            //declare array elements

    //Get the elements of the array
    printf("Enter the elements of the array:\n");
    for(int i=0; i < m; i++)                   //Run inner loop for rows
    {
        for(int j =0; j < n; j++)                   //Run outer loop for columns
        {
            printf("Element [%d][%d]: ", i, j);           //display the elements of array
            scanf("%d", &a[i][j]);                       //access array elements through user 
        }
    }
    
    printf("\nOriginal Array:\n");                             //display original array element
    printArray(m, n, a);

    //Replace each element with the 5th prime number
    replaceWith5thPrime(m, n, a);                                 

    printf("\nModified Array:\n");                       //Display modified array elements as replaced with 5th prime number
    printArray(m, n, a);

    return 0;
}

