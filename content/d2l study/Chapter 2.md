---
tags:
  - notes
draft: false
---

## Data Manipulation
### Some Definitions
A **tensor** represents a (possibly multidimensional) array of numerical values.
- by invoking arrange (n)->create a row vector of n from 0 to n-1
	`x = torch.arange(12, dtype=torch.float32)` 
- access a tensor's shape (the length along each axis)
	`x.shape` 
	*output*: `torch.Size([12])` 
- inspect the total number of elements in a tensor 
	`x.numel()` output: 12
- change the shape without changing the elements and values
	`X = x.reshape(3, 4)` which makes it becomes a matrix
	by placing -1 -> automatically infer one component of the shape.  In our case, instead of calling `x.reshape(3, 4)`, we could have equivalently called `x.reshape(-1, 4)` or `x.reshape(3, -1)`.
- create a tensor with all 1s / 0s
	`torch.zeros((2, 3, 4))` or `torch.ones((2, 3, 4))`
- creates a tensor with elements drawn from a standard Gaussian (normal) distribution with mean 0 and standard deviation 1.
	`torch.randn(3, 4)` 
- create by listing all values
	`torch.tensor([[2, 1, 4, 3], [1, 2, 3, 4], [4, 3, 2, 1]])` 
- sum all the elements
	`X.sum()`
### Indexing and Slicing
nearly same in Python 
`[-1]` selects the last row and `[1:3]` selects the second and third rows.
`X[a:b]` outputs the a-th row to the (b-1)th row (0-based)
`X[a,b] = 17` can modify the elements by specifying indices.
`X[:2, :] = 12 ` befor , 为修改元素的行索引范围 ；after , 为修改元素的列索引范围，不填则代表全部
### Openrations
- **element-wise operations**: These apply a standard scalar operation to each element of a tensor. 
The common standard arithmetic operators for addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`), and exponentiation (`**`) have all been _lifted_ to elementwise operations for **identically-shaped tensors** of arbitrary shape.
```python
x = torch.tensor([1.0, 2, 4, 8])
y = torch.tensor([2, 2, 2, 2])
x + y, x - y, x * y, x / y, x ** y
```
Output:
```python
(tensor([ 3.,  4.,  6., 10.]),
 tensor([-1.,  0.,  2.,  6.]),
 tensor([ 2.,  4.,  8., 16.]),
 tensor([0.5000, 1.0000, 2.0000, 4.0000]),
 tensor([ 1.,  4., 16., 64.]))
```
- **linear algebraic operations**
	- Hadamard product: A * B 
- **_concatenate_ operations**: stacking them end-to-end to form a larger one.
We need to provide a list of tensors and tell the system along which axis to concatenate.
e.g. `torch.cat((X, Y), dim=0), torch.cat((X, Y), dim=1)` dim=0 means concatenated along axis 0
- **logical operations** 
e.g ` X==Y ` will output a binary tensor via _logical statements_.
### Broadcasting
Work mechanism:
- expand one or both arrays by **copying elements along axes with length 1** so that after this transformation, the two tensors have the same shape;
-  perform an elementwise operation on the resulting arrays.
## Data Preprocessing
### Read the Dataset
1. CSV files(Comma-separated values), which storing of tabular (spreadsheet-like) data and can be loaded by pandas.
### Data Preparation
1.  separate out columns corresponding to input versus target values.
2.  missing values: which were replaced with a special `NaN` (_not a number_) value.
	handled by _imputation_ or _deletion_:  Imputation replaces missing values with **estimates** of their values(选取一个替代值/对同一类型赋上相同的值) while deletion simply **discards** either those rows or those columns that contain missing values.
### Conversion to the Tensor Format
```python
X = torch.tensor(inputs.to_numpy(dtype=float))
y = torch.tensor(targets.to_numpy(dtype=float))
X, y
```
