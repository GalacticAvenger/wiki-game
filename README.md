Overview

This README explains how the Gomoku bot is structured and functions within the context of a Gomoku game implemented in OCaml. The bot plays on a 15x15 board and aims to get five consecutive pieces in a row to win.

Bot Architecture

The bot is designed using the following key components:

Game Representation: The game state is represented as a combination of the current board, player pieces, and available moves. The Game module handles this representation, allowing the bot to query the board's state effectively.
Decision-Making Process: The bot's core decision-making is handled through various functions:
Available Moves: The bot queries the board for available positions using the available_moves function, which returns a list of all unoccupied positions on the board.
Winning Moves: Before making a move, the bot checks if it can win immediately using the winning_moves function. This function assesses all available moves and determines which would result in an immediate win.
Losing Moves: Similarly, the bot checks for potential losing moves that would allow the opponent to win on their next turn using the losing_moves function.
Minimax Algorithm: To enhance its strategy, the bot implements the Minimax algorithm. This algorithm evaluates possible future game states by:
Scoring current positions based on potential outcomes (win/loss).
Maximizing its own score while minimizing the opponent's score, effectively considering both players' optimal strategies.
Heuristic Evaluation: For situations where the game doesn't end immediately, the bot uses a heuristic evaluation function to assign scores to non-terminal game states based on the number of consecutive pieces and potential threats from the opponent.
Functionality

Key Functions
available_moves: Identifies all empty positions on the board where a player can place their piece.
winning_moves: Returns all positions that, if played, would allow the bot to win on the next turn.
losing_moves: Identifies moves that would allow the opponent to win on their next turn.
evaluate: Evaluates the current state of the game, returning whether it is ongoing, a win for one of the players, or an illegal move.
minimax: Implements the Minimax algorithm to look ahead several moves and choose the optimal play based on potential future outcomes.
Example Usage
Initialize Game: Start a new Gomoku game by creating an instance of the game board.
Bot Play: Call the bot's decision-making function with the current game state and its assigned piece (X or O).
Play Move: Execute the move returned by the bot in the current game state.
Conclusion

The Gomoku bot intelligently navigates the game by assessing available moves, predicting future outcomes, and employing strategic decision-making through the Minimax algorithm. By considering both winning and losing conditions, the bot aims to play optimally against human opponents or other AIs.
