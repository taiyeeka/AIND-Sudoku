# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: For a pair of boxes to be a naked twins, the necessary and sufficient condition is to satisfy all of the following:
(i) the boxes belong to the same unit (i.e. a row, a row, a principal 3x3 subsquare or a main diagonal);
(ii) they share the same two possible values (out of 1 to 9).
Each of the above can be viewed as contraints for us to search for the Naked Twins from the 9x9 board.
Naked Twins, once found, is itself a constraint to a Sudoku, which shall refer to as a naked-twins-constraint.
 
P.S. Note that the constraint naked-twins-constraint both belong to a more general class of constraints that "N box(es) within a unit all contain a subset of that N values".

 
# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: Diagonal Sudoku differs from a regular Sudoku by an additional constraint that the numbers 1 to 9 should all appear exactly once in each of the two main diagonals.

The two constraints introduced in class (namely, strategy 1 of elimination and strategy 2 of only choice) can be enhanced by consider also the main diagonals.

Enforcing naked-twins-constraints, and these two constraints will reduce the search space. Before getting into the any search step, a puzzle should be reduced until none of the constriants give further reduction.

Then we shall implement a depth first search (DFS) by calling a search function recursively. If a feasible solution is found, the search is terminated. Otherwise, it will proceed to search the entire (reduced) search space to return a false value, indicating no solution exist.

P.S.
Since the DFS summitted won't proceed to find more solution, the uniqueness of solution is not guaranteed.
### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

