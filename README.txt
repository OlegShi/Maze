# Maze
A maze solver for the "Advanced Topics in Programming" course in TAU (implemented in C++)

implemented using C++ smart pointers to avoid direct heap memory allocation and deallocation - using std::make_unique and std::make_shared appropriately.
includes 2 player algorithms as .so (shared objects) so that Player algorithms can be loaded dynamically.
using threads to run simultaneously different player algorithms on diffrent mazes.


Command line parameters:
the command line should be as follows:
match [-maze_path <path>] [-algorithm_path <algorithm path>] [-output <output path>] [-num_threads]
  
The maze input file is a text file in the following format:
Line 1: maze name  
Line 2: MaxSteps=<num> MaxSteps for solving this maze. We assume different mazes may require different MaxSteps.
Line 3: Rows=<num> Number of Rows in maze
Line 4: Cols=<num> Number of Cols in maze
Lines 5 and on: the maze itself, as described below
  
 -- # -- represents a wall
 -- space	-- represents a pass
 -- @	-- represents the player in the maze (initial position of the player)
 -- $	-- represents the end of the maze (the treasure that we seek)
 
Player Movement in the Maze:
the player doesn’t know the dimensions of the maze nor his own ‘location’!
The player can move in any of the four directions: UP, RIGHT, DOWN, LEFT.
The player can also choose to set a BOOKMARKS in the current position. each bookmark that is set by the player gets a sequential number starting from 1. This helps the player to navigate throughout the maze.
Setting a bookmark is considered a move, so the player stays in its current location during this turn.
The player can’t move into a wall.
The player can move beyond the last line / last column - that would bring the player back to the first (zero indexed) line / column respectively, without any special notice, as long as there is no wall preventing this “tunneling”. Same goes for getting “back” beyond line/column 0.
 
The output file is a text file , inside the file there would be a line per each step done by the player, from the options: U, R, D, L, B
Last line in the file would be: X  -- in case of failing to solve the maze
Or: ! -- in case the maze was solved.

