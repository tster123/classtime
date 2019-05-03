# Mazer
Mazer is a game in which a player attempts to traverse a maze arranged as a grid. 
Each space in the maze is either empty or contains an obstacle.

The `Mazer` class, shown below, uses a two-dimensional array to represent the maze.
```
public class Mazer
{
  /** maze[r][c] represents the space at row r and column c in the maze.
   *  Empty spaces are represented by null. */
  private String[][] maze;

  /** Constructs a maze with the specified number of rows and columns.
   *  Each space in the maze has:
   *   - a 10% chance of containing a "|"
   *   - a 20% chance of containing a "/"
   *   - a 20% chance of containing a "\"
   *  except that an obstacle may not be placed in position [r][c] if
   *  position [r][c-1] already contains an obstacle.
   *  Obstacles are placed from left to right in each row of the maze.
   *  @param rows the number of rows
   *  @param cols the number of columns
   *  Precondition: rows >= 3 && cols >= 5
   */
  public Mazer(int rows, int cols)
  { /* to be implemented in part (a) */ }

  /** @param startRow the player's starting row
   *  @return true if a player will win by starting at startRow, false otherwise
   *  Precondition: 0 <= startRow && startRow < maze.length
   *  Postcondition: the state of this object is unchanged
   */
  public boolean willWin(int startRow)
  { /* to be implemented in part (b) */ }

  // There may be instance variables, constructors and methods that are not shown.
}
```
# Part (a)
Write the constructor for the `Mazer` class. 
The constructor initializes the maze instance variable to a two-dimensional array with the given number of rows and columns. 
Each space in maze has a 10% chance of containing a "|", 
a 20% chance of containing a "/" and a 20% chance of containing a "\\" except that a space may not contain an obstacle 
if the space one column to the left already contains an obstacle. 
Obstacles are placed from left to right in each row of maze.

For example, a `Mazer` object created with the call `new Mazer(5, 8)` could have maze initialized with the following values.

| |0|1|2|3|4|5|6|7|
|-|-|-|-|-|-|-|-|-|
|0|null|null|"\\"|null|null|null|null|"/"|
|1|null|null|"/"|null|null|null|null|null|
|2|null|"\\"|null|null|null|"/"|null|null|
|3|"&#x7c;"|null|null|"/"|null|"\\"|null|null|
|4|null|null|null|null|"/"|null|"\\"|null|

Complete the Mazer constructor below.
```
/** Constructs a maze with the specified number of rows and columns.
   *  Each space in the maze has:
   *   - a 10% chance of containing a "|"
   *   - a 20% chance of containing a "/"
   *   - a 20% chance of containing a "\"
   *  except that an obstacle may not be placed in position [r][c] if
   *  position [r][c-1] already contains an obstacle.
   *  Obstacles are placed from left to right in each row of the maze.
   *  @param rows the number of rows
   *  @param cols the number of columns
   *  Precondition: rows >= 3 && cols >= 5
   */
  public Mazer(int rows, int cols)
```

# Part (b)
Write the `willWin` method, which determines whether a player starting at a given row will win.

The player starts on the left side of the maze (column 0) at the given row (startRow). Each turn the player repeats the sequence of steps below, in order, until the player wins or loses.

1. If there is an obstacle at the player’s current position, the player handles it as described in the table below.

|Obstacle|Effect|
|--------|------|
|"/"|The player moves one row higher in the maze. (The player’s row position is decreased by 1.)|
|"\\"|The player moves one row lower in the maze. (The player’s row position is increased by 1.)|
|"&#x7c;"|The player loses.|

2. If the player’s row is not valid in the maze the player loses.
3. The player moves one column right in the maze. (The player’s column position is increased by 1.)
4. If the player’s column is not valid in the maze the player wins.

The table below shows the paths that players starting at each row would take through the maze constructed in part (a). 
Each player is represented by a P followed by the number of the row at which that player started. 
(Note that the player’s positions are not stored in the maze `array`.) 
Obstacles are shown but the value `null`, representing an empty space, is not shown.

| |0|1|2|3|4|5|6|7|
|-|-|-|-|-|-|-|-|-|
|0|P0|P0|P0 "\\"|P1|P1|P1|P1|"/" P1|
|1|P1|P1|P1 "/"|P0|P0|P0|P0 P2|P0 P2|
|2|P2|P2 "\\"| | |P2|P2 "/"| | | 
|3|P3 "&#x7c;"| |P2|P2 "/"| |P4 "\\"| | |
|4|P4|P4|P4|P4|P4 "/"| |P4 "\\"| |

A player starting at row 0 would win because the player’s column index would become 8 on the player’s 8th turn. A player starting at row 2 would win for the same reason.

A player starting at row 1 would lose because the player’s row index would become -1 on the player’s 8th turn.

A player starting at row 3 would lose because the player encountered a "|" on the player’s first turn.

A player starting at row 4 would lose because the player’s row index would become 5 on the player’s 7th turn.

Complete method willWin below.
```
/** @param startRow the player's starting row
   *  @return true if a player will win by starting at startRow, false otherwise
   *  Precondition: 0 <= startRow && startRow < maze.length
   *  Postcondition: the state of this object is unchanged
   */
  public boolean willWin(int startRow)
  ```
