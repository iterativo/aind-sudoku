# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: In `reduce_puzzle`, as we process the puzzle's state in the `values` dictionary, we can add a new strategy for the Naked Twins approach besides the original ones: `eliminate` and `only_choice`. In other words, `values` is now processed through 3 sets of constraint strategies: first the *eliminate* strategy, second the the *only choice* strategy, and finally the (new) *naked twins* strategy. Each strategy may produce a new (more constrained) puzzle state, which in turn is fed to the following strategy in the chain. This process is called *constraint propagation*. To arrive to a solution, we iterate through this process until the puzzle cannot be constrained any further.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: At the beginning of the solution, we build a `list` called `unitlist` that contains the sudoku units for which the constraint strategies are applied. Originally, this list was made up of the traditional sudoku units (`row_units + column_units + square_units`). In order to support diagonal sudoku, we just need to update this list with the *diagonal sudoku* list, resulting in `row_units + column_units + square_units + diag_units` (Note: the diagonal sudoku list is simply made up of the sudoku boxes that make up the 2 diagonal lines crossing the sudoku grid). With such change, since the `unitlist` is used by each one of our already implemented constraint strategies (*elimination*, *only choice*, and *naked twins*), effectively we end up incorporating diagonal sudoku rules into our constraints. 

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

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

