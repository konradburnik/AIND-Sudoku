# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: In the naked twins technique, we are propagating the following constraint: in the same unit, if there are pairs of boxes with exactly two entries and exactly the same values then these two values have to be locked within these two boxes. These values can then be eliminated from all other boxes in the same unit due to the constraints by definition of unit (see answer to next question). To implement this, we create an additional function `naked_twins` in `solution.py` which applies the rules of naked twins elimination. Every call to this function will do this elimination step for all the found naked twins pairs. In the existing `reduce_puzzle` we just add this call alongside `eliminate` and `one_choice` since `reduce_puzzle` is our constraint propagation procedure.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: For implementing this step we can extend the code from the lessons and can be found in `solution.py`. To gracefully add this new constraint which will be propagated together with all the already implemented constaints we do the following. A unit by definition can contain each of the values 1 to 9 only once. The existing code from the lessons properly handles the already defined units correctly so we define two new units: the `diagonal_unit` and `anti_diagonal_unit` and add them to the list of available units, the `unitlist`. Now, our new constraint sounds really like the old one: in all units, all the values from 1 to 9 can appear only once. The only difference is our definition of unit. We can leave the rest of the logic intact since after adding `diagonal_unit` and `anti diagonal_unit` to the `unitlist` and since the existing logic is written in terms of units, it will automatically take care of these new units in an analogous way as the previously defined ones. However, unrelated to this assignment part, and to make the solver better, we also add-in a call to the naked twins procedure from the first part of the assignment.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - Code from the lessons augmented with the solution code. Main caller to the solver.
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

