# Sudoku-Solver
Introduction:

The approach to building an algorithm for solving the sudoku, started by reading the section Contraction Satisfaction Problems from (Norvig, 2020).
Solving Sudoku Puzzles
The problem I have to solve today is to program a software that could resolve Sudoku with multiple level of difficulties. Some have valid and unqiue solutions and other are either invalid grids or have unsolvable.
Sudoku is popular game played daily by thousands of enthusiastic numberphile.

Method:

There multiple informed search algorithms that could be deployed to solve sudoku, like local search methods and particularly simulated annealing algorithm and genetic algorithm. This sudoku solver uses techniques followed generally to resolve Constraint Satisfaction Problems (CSP), including:
Depth-first search with backtracking algorithm: this algorithm builds candidates to the solutions, and abandons a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution [1]. This would eliminate the need for trying many invalid solutions. This limits the search space which usually makes the backtracking algorithm more efficient than a pure brute-force search [2]. Backtracking algorithm is best described as a method of organized trail and errors.

Constraint satisfaction propagation. this solver implements one kind of local consistency, namely node consistency. After finding the location of candidate empty cells, the solver picks a candidate that has the fewest remaining possible values in its domain (minimum residual heuristic value, MRV) and pass it into an express function. This function looks through the variable domain and return a list of possible value respecting all unary house constraints (row, column, square).

Human solving technique: difficult level sudoku calls to use advanced solving strategies that would perform candidate elimination hence reduce backtracking workload. Solving strategies, such as hidden singles, naked singles and naked pairs are referred to as human solving techniques [2]. Implementation of hidden singles technique is inside the code HOWEVER it is not actively called inside the solver because of incomplete integration. The function "hidden singles" is looking for candidates of hidden singles per row and column, update sudoku, call the function recursively until no more hidden singles are detected, return the new grid in order to continue with backtracking algorithm.

Results:

The algorithm solves all provided sudokus. Sudokus levels very-easy to medium take on average ~0.02s on my machine, and hard ones range from ~1.14-300s, with hard invalid ones reaching up to ~400s.

Area for improvement:

To improve overall performance and reduce the overly reliance on backtracking algorithm
Implement AC-2 algorithm [3] to ensure arc consistency in a way that each cell's possible values are consistent with admissible value of the second cell.
Complete integration of hidden singles and implement other human solving technique, like naked singles and naked pairs.

Conclusion:

While a brute-force approach is resource draining, a backtracking search algorithm can solve complex sudokus. Human solving technique would improve performance however this requires hardwiring these rules through introducing new 'constraints'.

Reference:

[1] Gurari, E., 1999. CIS 680: DATA STRUCTURES: Chapter 19: Backtracking Algorithms. Archived from the original on 17 March 2007.

[2] LINDBERG, J., STEIER, M., 2015. Efficiency of the hybrid AC3-tabu search algorithm for solving Sudoku puzzles. DEGREE PROJECT, IN COMPUTER SCIENCE , FIRST LEVEL STOCKHOLM, SWEDEN 2015 . Available from http://www.diva-portal.org/smash/get/diva2:810999/FULLTEXT01.pdf [Accessed 19 September 2021].

[3] Russell, S. and Norvig,P. 2002. Artificial Intelligence: A Modern Approach,Third Edition, P209.Pearson Education, Limited
