+++
date =2024-03-10T20:20:20-04:47
+++
# Backtracking
Any time you have a problem that is solved by a series of decision, you might make a wrong decision. When you realize that you have to backtrack to a place where you made the decision and try something else. It's usually associated to recursion.

# The Backtracking Blueprint
Consider these 3 keys to achieve solutions when dealing with backtracking problems. Also consider sudoku as the example.

**Choice**: Map the choices that you have to handle the problem. e.g. we choose numbers in each cell, so the solve function may handle a row and a column (cell location). We can break down into rows as the base case.
**Constraints**: Apply the conditions of the problem. e.g. row, column and grid validation, it may have only one for each. If valid, then recurse on your decision.
**Goal**: Reach base cases. e.g. there's no more empty cells.

### Code
First we will use the keys to build a primitive structure of our algorithm.
```
# Sudoku
def solve(row, col, board):
    # Goal
    if not emptyCell:
        return True

    # Choice
    for i in range(9):
        board[row][col] = i;

        # Applying constraints
        if validPlacement(row, col, board):
            # Recurse over decision
            if solve(row, col+1, board):
                return True

      # If it's not a good choice
      board[row][col] = 0
```
Now the complete solution is like this.
```
def isValid(board, row, col, num):
    for i in range(9):
        if board[row][i] == num or board[i][col] == num:
            return False

    starRow, startCol = 3 * (row // 3), 3 * (col // 3)
    for i in range(3):
        for j in range(3):
            if board[startRow + i][startCol + j] == num:
                return False
    return True

def findEmptyCell(board):
    for i in range(9):
        for j in range(9):
            if board[i][j] == 0:
                return i, j
    return None

def solve(board):
    emptyCell = findEmptyCell(board)
    if not emptyCell:
        return True
    row, col = emptyCell

    for num in range(1, 10):
        if isValid(board, row, col, num):
            board[row][col] = num

            if solve(board):
                return True
            board[row][col] = 0

    return False
```
