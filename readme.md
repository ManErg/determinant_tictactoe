# Determinant Tic-Tac-Toe
##### Ian Miller
##### Spring, 2018
#
Determinant Tic-Tac-Toe(DT) was a game designed to be a math challenge. In the game, two players will take turns marking out fields in a 3x3 matrix, much in the style of tic-tac-toe. The catch, however, is that
neither player is aiming for three-in-a-row of 'x's or 'o's. Rather, each player will mark their fields with '1's or '0's respectively. The player writing down '1's aims for the matrix to have a determinant of 1, after all fields have been filled. This player wins if she succeeds and loses otherwise.


Given a finite number of outcomes and set number of turns, DT is probably not a fair game. The question is to prove which player has an advantage. In addition to providing a pure math answer, I saw DT as an opportunity to practice finding solutions to abstract problems.
#
##### Methodology
This methodology of this solution is to exhaustivbely play iteratively through every possible scenario of just one strategy for one player. If every game turned up winning for the tested strategy, then the player able to utilize it has a decisize advantage; he will always win if he plays correctly. There may be more winning strategies, but finding even one is sufficient.

This is not the most elegant solution, but given how few possible games need to be played, it's adequate.
We will test the first player placing a '1' in each of nine fields, but the second player will always have a fixed response since they are using a strategy. With two fields occupied, there is only seven fields remaining for the first player to place their second '1'. Carried on in this way there should 945 uniqe games played.

![equation](https://latex.codecogs.com/gif.latex?%5Csum_%7Bi%3D0%7D%5E4%20f%282i&plus;1%29%3D945)

This means, if ever we can generate 945 unique games, where the second player has made the same moves consistently in response to identical board/matrix states, then we have found a winning strategy.

I also have a more elegant proof that relies on isomorphs instead of raw computation. I may add it to the readme later, but for the time being I anticipate zero interest. 

## Installation and Use
Preserve directory structure, call test_strategy.py using your interpreter.

Each of the 945 unique games will be obnoxiously printed out and following confirmation that each was printed, each game was unique, and a bool tied to whether or not player one ever won a game will follow.

## Organization
Game is an abstract class with some basic game functionality.

TicTacToe is a Game. Its members represent the various board states of a game of DT.

TwoPlayerSimulator simulates playing two player games. TwoPlayerSimulator assumes one strategy is a control strategy and will provide all possible moves at each step through of a game. It will use recursion to create branches - copies of the game at each control strategy turn, then make a uniqe move for each control player. The fixed response by the test strategy player will be made for each, then a new set of branches will be generated for each game. The stop case is the completion of a game.
This is similar to using recursion to find the max depth of a binary tree, only we are creating big expensive objects all along the way :)

Strategy is an abstract class with containers for all possible moves in a game and all legal moves for a given game state.

StrategyTTO is a Strategy. It initializes move containers appropriately for DT.

ControlStrategyTTO and TestStrategyTTO inherit from StrategyTTO and return the best moves for any given game state. ControlStrategyTTO should return all legal moves using an iterator.

When the solution is run, an instance of each strategy is initialized and used to construct a TwoPlayerSimulator.# Determinant Tic-Tac-Toe

