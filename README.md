# 8-queen
def print_board(board):
    for row in board:
        print(" ".join("Q" if col else "." for col in row))
    print("\n")

def is_safe(board, row, col):
    # Check column
    for i in range(row):
        if board[i][col] == 1:
            return False
    
# Check upper-left diagonal
  i, j = row, col
    while i >= 0 and j >= 0:
        if board[i][j] == 1:
            return False
        i -= 1
        j -= 1

   # Check upper-right diagonal
  i, j = row, col
    while i >= 0 and j < 8:
        if board[i][j] == 1:
            return False
        i -= 1
        j += 1

  return True

def solve_n_queens(board, row):
    if row == 8:
        print_board(board)
        return True  # Return True to stop at one solution
        # return False to continue finding all solutions

  for col in range(8):
        if is_safe(board, row, col):
            board[row][col] = 1  # Place queen
            if solve_n_queens(board, row + 1):
                return True
            board[row][col] = 0  # Backtrack
    return False

# Create empty 8x8 board
board = [[0 for _ in range(8)] for _ in range(8)]
solve_n_queens(board, 0)
