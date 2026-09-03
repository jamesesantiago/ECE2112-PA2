# ECE-2112-PA2

**By: James Eon M. Santiago | 2ECE-B**

This Repository Contains the Programming Assignment #2 for the Course "Advanced Computer Programming and Algorithms", which includes three python problems related to Module 2 - Numerical Computing with Python (NumPy).

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **(A) Reproducible Normalization Problem**

Create a 5x5 array of random integers between 10 to 100 using a set seed, then normalize the value using mean and standard deviation.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Create a 5x5 ndarray named **X** with random integers ranging from 10 to 100.

    `np.random.seed()` - is a seed to ensure that the generated numbers are reproducible every time.

    `np.random.randint()` - generates a array with random integers.
```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
X
```

2. Normalize the array
   
   `.mean()` - Calculates the mean ($\overline{x}$) of all 25 elements in the array.
   
   `.std()` - Calculates the population standard deviation ($\sigma$) of the array.
   
   Applying the formula `(X - X.mean()) / X.std()` scales the data to have a mean of 0 and a standard deviation of 1.
   
   The `np.save()` function saves the resulting array to a file named `X_normalized.npy`.

Using this, we can define the code as:

```python
X_normalized = (X - X.mean()) / X.std()
np.save('X_normalized.npy', X_normalized)
```

Therefore, the final code should look like: 

```python
np.random.seed(2112)
X = np.random.randint(10 ,101, size=(5,5))
X
X_normalized = (X-X.mean())/X.std()
np.save('X_normalized', X_normalized)
X_normalized
print("Normalized X Mean:" , X_normalized.mean())
print("Normalized X Standard Deviation:",X_normalized.std())
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **(B) Cubes Divisible by 4 Problem**

Create a 10x10 array containing the cubes of the first 100 positive integers and filter out the numbers which are divisible by 4

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Generate the first 100 positive integers, cube each element, and reshape into a 10x10 array.

   `np.arange(1, 101, 1)` - Creates an array containing positive integers from 1 to 100.

   `np.power(..., 3)` - Cubes every element in the array.

   `.reshape(10, 10)` - Converts the 1D array into a 2D 10x10 ndarray.

```python
C = np.power(np.arange(1, 101, 1), 3).reshape(10, 10)
```

2. Filter elements using a Boolean condition and save the result.

   The condition `C % 4 == 0` selects elements divisible by 4 while preserving row-major selection order.

Combining all these would result to:

```python
div_by_4 = C[C % 4 == 0]
np.save('div_by_4.npy', div_by_4)
div_by_4
```

The final code should look like:

```python
C = np.power(np.arange(1,101,1), 3).reshape(10,10)
C
div_by_4= C[C%4==0]
np.save('div_by_4',div_by_4)
div_by_4
print("Number of Elements that are divisible by 4: " ,np.size(div_by_4))
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **(C) Above-Mean Squares Problem**

Create a 6x6 array containing the squares of the first 36 positive integers, find the average value of the matrix and filter all the numbers greater than the mean.
---

1. Generate the squares of the first 36 positive integers and reshape them into a 6x6 matrix.

   `np.arange(1, 37, 1)` - Creates an array of integers from 1 to 36.

   `np.power(..., 2)` - Squares each integer in the array.

```python
S = np.power(np.arange(1, 37, 1), 2).reshape(6, 6)
```

2. Compute the mean of the array **S**.

   `.mean()` - Calculates the average of all the elements in the matrix.

```python
S_mean = S.mean()
```

3. Filter the array for elements strictly greater than **S_mean** and save the array.

   The Boolean indexing `S[S > S_mean]` extracts all elements strictly greater than the calculated mean.

Combining this would give us a defined function and checks:

```python
above_mean = S[S > S_mean]
np.save('above_mean.npy', above_mean)
```

The final code should look like:

```python
S = np.power(np.arange(1,37,1),2)
S
S_mean = S.mean()
S_mean
above_mean = S[S>S_mean]
np.save('above_mean',above_mean)
above_mean
```

Thanks for reading.
