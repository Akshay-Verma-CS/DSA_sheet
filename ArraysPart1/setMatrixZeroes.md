
# Set Matrix Zeroes - LeetCode Problem

## Problem Description
Given an `m x n` matrix. If an element is 0, set its entire row and column to 0. Do it in-place.

Follow up:
- A straight forward solution using O(mn) space is probably a bad idea.
- A simple improvement uses O(m + n) space, but still not the best solution.
- Could you devise a constant space solution?

## Solution in Python

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        self.matrix = matrix
        self.countRows = len(matrix)
        self.countColumns = len(matrix[0])
        self.traverseMatrix()
        return self.matrix
    
    def traverseMatrix(self):
        rowsToSetZero = []
        columnsToSetZero = []
        for i in range(self.countRows):
            for j in range(self.countColumns):
                if self.matrix[i][j] == 0:
                    rowsToSetZero.append(i)
                    columnsToSetZero.append(j)
        for k in rowsToSetZero:
            self.setRowZero(k)
        for k in columnsToSetZero:
            self.setColumnZero(k)
        
    def setRowZero(self,rowIndex):
        for i in range(self.countColumns):
            self.matrix[rowIndex][i] = 0
    
    def setColumnZero(self,columnIndex):
        for i in range(self.countRows):
            self.matrix[i][columnIndex] = 0
```

This Python solution provides a method to set the rows and columns to zero if any zero is found in the matrix. It is not optimized as it uses additional memory for tracking rows and columns to be set to zero.

