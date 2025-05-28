# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
### Step 1: Input the Matrix
Read the number of unknowns n.
Create an (n x (n+1)) augmented matrix to hold coefficients and constants.
Populate the matrix with user input.

### Step 2: Forward Elimination
Goal: Convert the matrix into an upper triangular form (all elements below the main diagonal become zero).
For each row i from 0 to n-1:
Pivot Check: If the diagonal element a[i][i] is 0, the method can't proceed (division by zero) – exit with an error.
For each row j below i (from i+1 to n-1):
Compute the elimination ratio: ratio= a[i][i]a[j][i]​
Subtract ratio * row i from row j to eliminate the element at column i: a[j][k]=a[j][k]−ratio⋅a[i][k]for all k∈[0,n]

### Step 3: Back Substitution
Now the matrix is upper triangular. Solve for variables starting from the last row.
Solve the last variable:
x[n−1]= a[n−1][n]/a[n−1][n−1]​
For i from n-2 down to 0:
Initialize: x[i]=a[i][n] Subtract the known values: x[i]=x[i]−a[i][j]⋅x[j]for all j∈[i+1,n−1] Finally: x[i]= x[i]/a[i][i]​

### Step 4: Output the Solution
Print each variable x[i] with two decimal places.

## Program:
```
import numpy as np
import sys

# Reading number of unknowns
n = int(input())

# Making numpy array of n x (n+1) size and initializing to zero for storing augmented matrix
a = np.zeros((n, n+1))

# Making numpy array of n size and initializing to zero for storing solution vector
x = np.zeros(n)

# Reading augmented matrix coefficients
for i in range(n):
    for j in range(n+1):
        a[i][j] = float(input())

# Applying Gauss Elimination
for i in range(n):
    if a[i][i] == 0.0:
        sys.exit('Divide by zero detected!')

    for j in range(i+1, n):
        ratio = a[j][i] / a[i][i]
        
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]

# Back Substitution
x[n-1] = a[n-1][n] / a[n-1][n-1]

for i in range(n-2, -1, -1):
    x[i] = a[i][n]
    
    for j in range(i+1, n):
        x[i] = x[i] - a[i][j] * x[j]

    x[i] = x[i] / a[i][i]

# Displaying solution
for i in range(n):
    print('X%d = %0.2f' % (i, x[i]), end=' ')
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: MIDHUN S
RegisterNumber: 212224230158
*/
```

## Output:
![Screenshot 2025-04-26 113926](https://github.com/user-attachments/assets/0b97b3c2-59db-4052-bcb1-80cbe32df3f2)



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

