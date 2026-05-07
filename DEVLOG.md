# DEVLOG

## Entry 1 — Starter code review
Issue:Needed to understand the starter code and identify what parts were already provided.  
Symptoms / observations:The maze generation, boundary cell selection, maze printing, and path printing were already implemented, but DFS and the DFS call in `main()` were missing.  
Attempts made: Read through `generateMaze()`, `chooseBoundaryCell()`, `printMaze()`, and `printPath()` to understand how the maze and parent arrays worked.  
Final resolution: Determined that only `dfs()` and the DFS call / result handling in `main()` needed to be completed.

## Entry 2 — DFS base cases
Issue: Needed to stop DFS from exploring invalid cells.  
Symptoms / observations: Without checks, recursion could go outside the maze, step into walls, or revisit cells repeatedly.  
Attempts made: Added checks for out-of-bounds coordinates, wall cells, and already-visited cells at the start of `dfs()`.  
Final resolution: DFS now immediately returns `false` for invalid moves.

## Entry 3 — Marking visited cells
Issue: Needed to prevent repeated exploration of the same open cell.  
Symptoms / observations: Recursive DFS can revisit cells and cause unnecessary repeated work if visited cells are not tracked.  
Attempts made: Used the provided `visited` 2D vector and marked each valid cell as visited after passing the base checks.  
Final resolution: DFS now avoids revisiting cells and explores each reachable cell at most once.

## Entry 4 — Parent tracking for path reconstruction
Issue: Needed `printPath()` to reconstruct the path from exit back to entrance.  
Symptoms / observations: `printPath()` depends on correct `parent_r` and `parent_c` values for every visited neighbor on the successful path.  
Attempts made: Assigned the current cell as the parent of the next cell before making the recursive DFS call.  
Final resolution:Parent arrays are now filled correctly, allowing the final path to be printed.

## Entry 5 — Detecting the exit
Issue: Needed DFS to stop searching once the exit was found.  
Symptoms / observations: If there is no exit check, DFS would keep exploring even after reaching the destination.  
Attempts made: Added a condition to compare the current row and column with the exit coordinates.  
Final resolution: DFS now returns `true` immediately when the exit cell is reached, and that `true` value propagates back through the recursive calls.

## Entry 6 — Connecting DFS in main
Issue: The starter code still had commented placeholder lines in `main()`.  
Symptoms / observations: The program generated and printed the maze, but it would not actually solve it until DFS was called.  
Attempts made: Replaced the commented `bool found = dfs(...)` line with an actual DFS call and added the `if (found)` / `else` block.  
Final resolution: The program now prints the path when a route exists and prints `No path exists.` when the exit cannot be reached.

## Entry 7 — Compilation and testing
Issue:Needed to verify that the program compiled and behaved correctly on random mazes.  
Symptoms / observations: Random maze generation can produce either solvable or unsolvable mazes, so both cases needed testing.  
Attempts made: Compiled with `g++ -std=c++17 main.cpp -o maze` and ran the program multiple times using small maze dimensions such as `5 5`.  
Final resolution:Confirmed that the program correctly prints a valid path when one exists and prints `No path exists.` otherwise.