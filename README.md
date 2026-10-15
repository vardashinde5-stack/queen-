Experiment No. 9
Title

Backtracking: 8 Queens Problem

Aim

To implement the 8 Queens Problem using the Backtracking technique and analyze its time and space complexity.

Program
#include <stdio.h>
#include <stdlib.h>

#define N 8

int board[N][N];

int isSafe(int row, int col)
{
    int i, j;

    // Check the same column
    for (i = 0; i < row; i++)
    {
        if (board[i][col] == 1)
            return 0;
    }

    // Check the upper-left diagonal
    for (i = row - 1, j = col - 1;
         i >= 0 && j >= 0; i--, j--)
    {
        if (board[i][j] == 1)
            return 0;
    }

    // Check the upper-right diagonal
    for (i = row - 1, j = col + 1;
         i >= 0 && j < N; i--, j++)
    {
        if (board[i][j] == 1)
            return 0;
    }

    return 1;
}

int solveNQueens(int row)
{
    if (row == N)
        return 1;

    for (int col = 0; col < N; col++)
    {
        if (isSafe(row, col))
        {
            board[row][col] = 1;

            if (solveNQueens(row + 1))
                return 1;

            // Backtrack
            board[row][col] = 0;
        }
    }

    return 0;
}

void printBoard()
{
    printf("\nSolution for 8 Queens Problem:\n\n");

    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            if (board[i][j] == 1)
                printf(" Q ");
            else
                printf(" . ");
        }
        printf("\n");
    }
}

int main()
{
    if (solveNQueens(0))
    {
        printBoard();
    }
    else
    {
        printf("No solution exists.\n");
    }

    return 0;]

Algorithm
Start the program.
Initialize an 8 × 8 chessboard with all positions set to zero.
Start placing queens from the first row.
Check each column in the current row to determine whether placing a queen is safe.
Verify that no queen exists in the same column or either upper diagonal.
If the position is safe, place a queen in that position.
Recursively attempt to place a queen in the next row.
If a solution cannot be found, remove the previously placed queen. This process is called backtracking.
Continue trying other columns until a valid arrangement is found.
When queens have been placed successfully in all eight rows, display the chessboard.
Stop the program.
Time Complexity
Operation	Time Complexity
Initializing the chessboard	O(N²)
Checking whether a position is safe	O(N)
Exploring possible queen placements	O(N!) (standard upper-bound analysis)
Overall Time Complexity	O(N!) (standard upper-bound analysis)
Explanation

The 8 Queens Problem is solved using Backtracking by placing one queen in each row while ensuring that no two queens attack each other.

The isSafe() function checks the column and diagonals in O(N) time.
The algorithm explores possible queen placements recursively.
Whenever a placement leads to no solution, the algorithm removes that queen and tries another position.
Since one queen is placed in each row and columns cannot be repeated, the search has a standard O(N!) upper-bound analysis, with safety-check overhead included in the commonly stated bound.

Therefore, the commonly stated time complexity is:

Time Complexity = O(N!) (standard upper-bound analysis)

For the given problem, N = 8.

Space Complexity

The program uses the following data structures:

board[N][N] to store the chessboard.
The recursive function calls to explore possible queen placements.

The chessboard requires O(N²) space, while the recursion stack requires O(N) space.

Therefore:

Space Complexity = O(N²)

Applications
Solving constraint-satisfaction problems.
Understanding the Backtracking technique.
Solving puzzles involving restrictions on placements.
Scheduling tasks with conflicting constraints.
Exploring combinatorial search problems.
Learning recursive problem-solving techniques.
Advantages
Provides a systematic method for finding a valid solution.
Avoids exploring some invalid arrangements by checking constraints early.
Demonstrates the practical application of recursion and Backtracking.
Can be adapted to solve generalized N Queens problems.
Requires relatively little additional memory beyond the board and recursion stack.
Limitations
The number of possible arrangements grows rapidly as N increases.
The algorithm may explore many candidate placements before finding a solution.
The given program prints only one valid solution.
The program is specifically designed for an 8 × 8 chessboard.
The recursive approach may become computationally expensive for larger boards.
Conclusion

The 8 Queens Problem is solved using the Backtracking technique by placing eight queens on an 8 × 8 chessboard so that no two queens attack each other.

The algorithm places queens row by row, checks whether each placement is safe, and removes a queen whenever a placement prevents a valid solution.

The commonly stated time complexity is O(N!) under standard upper-bound analysis, and the space complexity is O(N²).

This experiment demonstrates how Backtracking can efficiently eliminate invalid choices while solving constraint-based problems. output image <img width="1536" height="1024" alt="queen" src="https://github.com/user-attachments/assets/4634d24d-4821-4da8-980c-6d11a34b51f8" />
