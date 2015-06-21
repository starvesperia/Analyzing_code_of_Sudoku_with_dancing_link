# Analyzing_code_of_Sudoku_with_dancing_link
Algorithm term project

The purpose of this project was finding out what is the dancing link and how to apply it to the sudoku.
First I found the paper -Knuth, Donald (2000). "Dancing links". The paper was saying this. In circular doubly linked list if there are nodes x, left and right node of node x, "x.left.right = x.right; x.right.left = x.left;" will remove the node x from the list. And to recover x to the list, we simply do "x.left.right = x; x.right.left = x;".
And then I found "Algorithm X" which can solve exact cover problem.
You might want to search about exact cover probelm.

Resultingly, I found the dancing link is the technique to implement "Algorithm X" efficiently, and "Algorithm X" is the solution of exact cover problem.
So I search the way how to apply "Algorithm X" to the sudoku.

There are four constraints 
1. Only 1 number can be in 1 square.
2. Same number can't be in same row.
3. Same number can't be in same column.
4. Same number can't be in same area.

To solve this, I used divide-and-conquer. First, I expressed 4x4 size sudoku puzzle in exact cover problem.

At row, Cand means candidate number, r means row, c means column.
So, there are 64 rows in 4x4 sudoku puzzle because there are four candidate numbers(1, 2, 3, 4), 4 rows and 4 columns.
There are 64 columns and each 16 columns is meaning four constraints.
First 16 columns are meaning the first constraint. For example, if you select (2,1,1) it means there is 2 in (1, 1). So 1, 3, 4 can't be in (1, 1) and you erase those nodes.
Second 16 columns are meaning the second constraint. If you select (3,1,1) , you will erase (3,1,2), (3,1,3) and (3,1,4).
Like this way, we can solve the 4x4 sudoku puzzle.

9x9 sudoku puzzle is just expansion of this 4x4 sudoku puzzle.
It can be expressed in exact cover problem which has 9x9x9 rows and 9x9x4 columns.

And then I found an open source code of sudoku solving code which using dancing link.

url : http://uaasoftware.com/blog/demos-tutorials/dancing-links-solving-sudoku/
