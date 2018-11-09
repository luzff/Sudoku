# Sudoku

Very small, clean and easy to use sudoku solver running on backtracking algorithm and written in Python 3. This solver will find ALL solutions. Thus it is very slow for sparsely given sudoku problems. 


## Algorithm
A sudoku can be represented by some array with 81(=9x9) entries.
We will represent the empty fields as ```0```.
```python
example = [
    1,2,3, 4,5,6, 7,8,9, 
    4,5,6, 7,8,9, 1,2,3, 
    7,8,9, 1,2,3, 4,5,6, 

    2,3,1, 5,4,7, 6,9,8, 
    5,4,7, 6,9,8, 3,1,2, 
    6,9,8, 2,3,1, 5,4,7, 

    0,0,0, 0,0,0, 0,0,0, 
    0,0,0, 0,0,0, 0,0,0, 
    8,6,4, 0,0,0, 0,0,0, 
]
```
A sudoku is called valid if no non-zero values occur twice in a row, a column or a block.

A soduku ```solution``` will be called the solution of the sudoku ```problem``` if 
1. all non-empty fields of ```problem``` are the same as the corresponding fields of ```solution``` and 
2. the solution has **no empty fields** and
3. both ```problem```and ```solution``` are **valid**. 


Alphabetical order.
-------------------
Imagine each soduku was a 81 digit number. The  **alphabetical order** is the order naturally induced by natural numbers. 
Check if first soduku is larger by typing ```is_larger(sudoku1, sudoku2) == True```.


Changable fields.
-----------------
Iterating over all 81 digits takes a lot of time. We can save a factor of 10^g operations, where g is the number of given digits, if we simply leave out all given fields. The remaining fields are called changeable. To find the next changeable field ```i``` that is smaller than some field ```index``` type ```i = last_changeable_field(sudoku, index)```.


Solving.
--------
We can write a function that calculates the alphabetically closest filled in sudoku using a brute force approach. This could of course be improved but the algorithm gives a runtime of a few seconds for most sodokus you can find in newspapers which is good enough in practise. 
Type ```solutions = solve(sudoku)``` to get a list of all solutions. If the sudoku is very sparsely given this will take a long time! Remember that the running time is about O( 10^(81-g) ).

Check ```len(solutions)``` to find out whether there is no solution (you might want to check ```problem_valid(sudoku)```), whether there is an exact solution ```len(solutions)==1``` or whether there are multiple solutions ```len(solutions)>1```. 
