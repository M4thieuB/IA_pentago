# Pentago: The game

The rules are simple. 

The goal is to **align 5 marbles** (horizontally, vertically or on the diagonal).

In order to do this, you play on a 6x6 size board which contains 4 3x3 size so-called "sub-board". These sub-boards have a particularity: they can rotate by 90 or -90 degrees.

>Now, how do you play?

You play turn by turn. During his turn, each player has to put a marble on the board and then rotate a sub-board by the direction of his choice (Remember 90 or -90 degrees). The game stops when a player has won or when it's a draw.

# In the program

First, to compile this program, copy this line in your terminal: 

```
gcc -W -Wall -std=c99 -O3 -o pentago_ia pentago.c
```

In this program, you play against a AI which is going to start.

To play, the program will indicate to you when it's your turn by the line:

```
Your move (format: 'x y'):
```
You have to indicate the coordinates of your move in the following format: "x y". (Example: I want to play in 2,3 then I will enter: `2 3`)

The coordinates are printed with the board but as a reminder: the `x-coodinate` represents the row and the `y-coordinate` represents the column.

Then, the following line appears on the screen: 
```
Your rotation (format: 'sub-board direction'):
```
Like above, you are going to enter the sub-board you want to rotate (from 0 to 3 where 0 is the one at the top left and 3 is the one at the bottom right) by the direction of your choice (1 for 90 degrees and -1 for -90 degrees). (Example: I want to rotate the sub-board at the top right by 90 degrees, I will enter: `1 1`).

# How I did it

The AI uses the Alpha_beta algorithm. In order to work, the algorithm try to create the pattern evaluated as the best, or the one that gives the most advantage in the current position.

This is why, I have an array of pattern (it is short because I check for symmetry and color symmetry too) where:

- 0 is an empty position
- 1 is a position owned by the player who is playing
- -1 is a position owned by the opponent

and at each pattern, an amount of points is associated: 100 being the highest score and then -100 being the lowest score.

Once these patterns are defined, the AI computes each position and stores the move that gives the best advantage for him. Further the game goes, bigger is the depth of the algorithm (that means the algorithm predicts more moves).
