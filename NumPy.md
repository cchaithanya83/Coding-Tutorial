---

## NumPy Tutorial

### Introduction
NumPy (Numerical Python) is a fundamental package for scientific computing in Python. It provides support for arrays, mathematical functions, linear algebra, random number generation, and more. This tutorial covers basic NumPy commands and functions to help you get started.

---

### Table of Contents
1. [Importing NumPy](#importing-numpy)  
2. [Creating Arrays](#creating-arrays)  
3. [Array Attributes](#array-attributes)  
4. [Indexing and Slicing](#indexing-and-slicing)  
5. [Array Operations](#array-operations)  
6. [Mathematical Functions](#mathematical-functions)  
7. [Reshaping Arrays](#reshaping-arrays)  
8. [Random Module](#random-module)  

---

### 1. Importing NumPy
```python
import numpy as np
```
The convention is to use `np` as an alias for NumPy.

---

### 2. Creating Arrays
```python
# From a list
arr = np.array([1, 2, 3])

# 2D array
arr2d = np.array([[1, 2], [3, 4]])

# Zeros and Ones
zeros = np.zeros((2, 3))
ones = np.ones((3, 3))

# Range of values
rng = np.arange(0, 10, 2)

# Evenly spaced values
lin = np.linspace(0, 1, 5)
```

---

### 3. Array Attributes
```python
arr.shape     # Dimensions
arr.dtype     # Data type
arr.ndim      # Number of dimensions
arr.size      # Total number of elements
```

---

### 4. Indexing and Slicing
```python
arr = np.array([10, 20, 30, 40, 50])
arr[1]       # 20
arr[1:4]     # [20 30 40]

# 2D indexing
arr2d = np.array([[1, 2], [3, 4], [5, 6]])
arr2d[1, 1]  # 4
arr2d[:, 0]  # [1 3 5]
```

---

### 5. Array Operations
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

a + b      # [5 7 9]
a * b      # [ 4 10 18]
a ** 2     # [1 4 9]
```

---

### 6. Mathematical Functions
```python
np.mean(a)      # Mean
np.median(a)    # Median
np.std(a)       # Standard deviation
np.sum(a)       # Sum
np.max(a)       # Max value
np.min(a)       # Min value
```

---

### 7. Reshaping Arrays
```python
arr = np.arange(6)       # [0 1 2 3 4 5]
arr.reshape((2, 3))      # [[0 1 2], [3 4 5]]
arr.ravel()              # Flattened array
```

---

### 8. Random Module
```python
np.random.rand(2, 3)       # 2x3 array with random values [0, 1)
np.random.randint(0, 10)   # Random integer between 0 and 9
np.random.seed(0)          # Set seed for reproducibility
```

---
