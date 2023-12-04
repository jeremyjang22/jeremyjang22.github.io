#### [Home](https://jeremyjang22.github.io) |  [Experience](../Experience.md) | [Projects](../Projects.md) | [Education](../Education.md)
___________
## Implementation of Little Go AI agent
Date: September 2023 - October 2023
### Description:

Implemented a GO agent for a 5x5 board. Played against other various agents (random, greedy, aggressive, alpha-beta, Q-learning, championship).

#### Game Details:
* Board deails:
    * 0 = empty point
    * 1 = black stone (Visually "X")
    * 2 = white stone (Visually "O")
* Black plays first
* Board size = 5x5
    * Max number of moves allowed = (n * n) - 1 = 24
* Komi = n / 2 = 2.5
* Enforced Rules:
    * Liberty (no suicide)
    * KO
* Passing allowed
* Max time per move = 10 seconds


#### End of Game Conditions:
* When player's turn exceeds time limit (10 seconds)
* When an invalid move is made (invalid placement, suicide, violation of KO-rule)
* When both players pass / two consecutive passes
* When the game exceeds the maximum amount of allowed moves (5*5 - 1 = 24 moves)

#### Winning Conditions:
* Partial Area Scoring: the number of occupied spaces by the respective player's stones (black/white)
* Final Scoring:
    * Black = partial area score
    * White = partial area score + komi
* If a player's time for a single move exceeds the limit (10 seconds), they lose the game
* If a player makes an invalid move, they lose the game
* If the game reaches the maximum steps allowed (24) or both players consecutively pass, the player with the higher final score is the winner

### Approach:

I implemented my agent with an **alpha-beta search + pruning strategy**, and factored the following into my heuristic:
* The difference in score, including komi
* The number of groups on the board
* Euler number (see [Erik van der Werf's Thesis](http://erikvanderwerf.tengen.nl/pubdown/thesis_erikvanderwerf.pdf) for a detailed explanation)
* The number of liberties
* The number of [eyes](https://www.pandanet.co.jp/English/learning_go/learning_go_7.html)

### Remarks:
* I was able to get a satisfiable win rate against the random, greedy, and aggressive agents, but was not able to beat the alpha-beta agent at a decent rate.
* I would really like to have implemented a Monte Carlo Tree Search or Neural Network, but that was beyond the scope of what we've learned in class so far.
* Reinforcement Learning would have been interesting to implement as well, but I didn't have enough time to implement it. 
* I think my heuristic might've been to complicated, as I've heard of other agents that performed better than mine using a simpler heuristic.

### Resources:
* [Erik van der Werf's Thesis](http://erikvanderwerf.tengen.nl/pubdown/thesis_erikvanderwerf.pdf)
* [MIGOS (also from Erik)](http://erikvanderwerf.tengen.nl/5x5/5x5solved.html)
* [Alpha-Beta Pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning)

