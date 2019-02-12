Bejeweled, for those unacquainted with it, is a popular game that consists of a square/rectangular grid of different-colored jewels. The game is played by swapping the positions of jewels that are horizontally or vertically adjacent to create chains of three or more jewels of the same color. You can refer to wikipedia for further gameplay details.

We can represent a bejeweled game grid in MokoM with an array of array of numbers, with different numbers representing different colors. Consider the following board for example:

array(
  array( 3 , 3 , 3 , 4 , 1 , 2 ),
  array( 0 , 0 , 3 , 2 , 4 , 4 ),
  array( 4 , 0 , 0 , 2 , 2 , 1 ),
  array( 1 , 3 , 4 , 2 , 4 , 0 ),
  array( 0 , 1 , 0 , 2 , 0 , 1 ),
  array( 2 , 2 , 2 , 4 , 1 , 3 ),
)
As previously noted, the objective of the game is to form chains consisting of three or more jewels of the same color that are either horizontally or vertically adjacent. The example game board above contains 3 such chains, highlighted in red below:

array(
  array( 3 , 3 , 3 , 4 , 1 , 2 ),
  array( 0 , 0 , 3 , 2 , 4 , 4 ),
  array( 4 , 0 , 0 , 2 , 2 , 1 ),
  array( 1 , 3 , 4 , 2 , 4 , 0 ),
  array( 0 , 1 , 0 , 2 , 0 , 1 ),
  array( 2 , 2 , 2 , 4 , 1 , 3 ),
)
Your task in this question is to write a function count_chains that accepts a bejeweled game board as described above (an array of array of numbers) and then counts and returns the number of chains in the given game board. Each continuous horizontal or vertical chain counts as a single chain, regardless of length. However if a horizontal chain intersects a vertical chain, they still count as separate chains. Some examples:
array(
  array( 0 , 3 , 3 ),
  array( 0 , 0 , 0 ),
  array( 0 , 1 , 4 )
)
The above has 2 chains (first column and second row).

array(
  array( 3 , 3 , 3 , 3 , 3 ),
  array( 0 , 0 , 1 , 2 , 1 ),
  array( 0 , 1 , 4 , 3 , 2 )
)
The above has one chain (first row)

You may assume that you are always given a proper game board: ie. an array of equal-length arrays of only integer values. The length and width of the board can however be arbitrary, the number of different colors of jewels is also arbitrary.

Your final solution should just define the count_chains function. You don't need to call it in any way, and you should not print anything. You may however define any number of helper functions to break down the task in a sensible way.

Example code the evaluator would run:

print count_chains(array(array( 0 , 3 , 3 ),array( 0 , 0 , 0 ),array( 0 , 1 , 4 )))

Example expected output:

2
