# Knight's Tour :chess_pawn:
The knight's tour is a sequence of moves of a knight on a chessboard such that the knight visits every square once. If the knight is able to visit every square and ends up on the beginning square as its last move, this is a complete knight tour.

My program written in **Java** and implements **Stacks** and **Backtracking** in order to find a solution for boards between 3x3 and 8x8.

## Instructions
Download both `KnightTour.java` and `KnightBoard.java`. The knight tour can be run by calling `$ java KnightTour n` where `n` is an `n x n` size board.
```
$ java KnightTour 5
Possible Knight Tour with max #squares visited in this (5x5) board:
+--+--+--+--+--+
| 1|10| 5|16|25|
+--+--+--+--+--+
| 4|17| 2|11| 6|
+--+--+--+--+--+
| 9|20|13|24|15|
+--+--+--+--+--+
|18| 3|22| 7|12|
+--+--+--+--+--+
|21| 8|19|14|23|
+--+--+--+--+--+

(Time to find this solution = 70.3757 milliseconds)
```
## Breakdown
- `KnightBoard`: Chessboard class is a 2D array that has `n` size, keeps track of the number of moves in `moveCount`, and current position of the knight in `currentX` and `currentY`. There are also some helper methods such as `printChessBoard`, `copyBoard`, and `move` (checks if a knights move to a specific position is valid). There are also setters and getters to modify `moveCount`, `currentX`, and `currentY` positions.
- `KnightTour`: Implements and prints a valid knight tour. This does not print all valid knight tours as the valid number of tours for a 6x6 board is 6,637,920 and the it only gets exponentially larger. The program essentially has all 8 moves of a knight listed out in two separate arrays `possibleRow` and `possibleCol`. It only adds valid moves from the current position to the stack. This for every single space that the knight can occupy until a board is found where `currentBoard.getMoveCount() == n * n` or if `n == 3 || n == 4` there is no solution where every space is visited so a solution with all but one space visited is valid.

## Visualization of the Stack
```
$ java KnightTour 3
Stack: Round 1
+--+--+--+
| 1|  |  |
+--+--+--+
|  |  |  |
+--+--+--+
|  |  |  |
+--+--+--+
Stack: Round 2 (two more possible moves are added to the stack)
+--+--+--+      +--+--+--+
| 1|  |  |      | 1|  |  |
+--+--+--+      +--+--+--+
|  |  | 2|      |  |  |  |
+--+--+--+      +--+--+--+
|  |  |  |      |  | 2|  |
+--+--+--+      +--+--+--+
Stack: Round 3 (explores all possible moves from the last board added to the stack)
+--+--+--+
| 1|  |  |
+--+--+--+
|  |  | 2|
+--+--+--+
| 3|  |  |
+--+--+--+
Stack: Round 4
+--+--+--+
| 1| 4|  |
+--+--+--+
|  |  | 2|
+--+--+--+
| 3|  |  |
+--+--+--+
Stack: Round 5
...
Stack: Round 6
...
Stack: Round 7
...
Stack: Round 8
+--+--+--+
| 1| 4| 7|
+--+--+--+
| 6|  | 2|
+--+--+--+
| 3| 8| 5|
+--+--+--+
