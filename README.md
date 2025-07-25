# RL_Easy21: An implementation of the game from David Silver's Reinforcement Learning Lectures

## Game description

- The game is played with an infinite deck of cards (i.e. cards are sampled
with replacement)
- Each draw from the deck results in a value between 1 and 10 (uniformly
distributed) with a colour of red (probability 1/3) or black (probability
2/3).
- There are no aces or picture (face) cards in this game
- At the start of the game both the player and the dealer draw one black
card (fully observed)
- Each turn the player may either stick or hit
- If the player hits then she draws another card from the deck
- If the player sticks she receives no further cards
- The values of the player’s cards are added (black cards) or subtracted (red
cards)
- If the player’s sum exceeds 21, or becomes less than 1, then she “goes
bust” and loses the game (reward -1)
- If the player sticks then the dealer starts taking turns. The dealer always
sticks on any sum of 17 or greater, and hits otherwise. If the dealer goes
bust, then the player wins; otherwise, the outcome – win (reward +1),
lose (reward -1), or draw (reward 0) – is the player with the largest sum.

## Method 1: Monte Carlo Control

- Run a large number of episodes of the game, keep track of the trajectory of the episode
- Following epsilon greedy policy improvement strategy.
- Update value function after the end of each episode, and follow first visit updates.

### Observations

The optimal policy found by the algorithm is to hit till your sum is 17 and after that its better to stick. The value function of the stick action shows that if your sum is greater than 10 and less than 17 ish, its bad to stick, matching the intuition that its bad to stick in that interval since the dealer sticks after his sum is less than 17. There is also another observation that the algorithm recommends us to stick in the starting, even though intuitively that is very bad. I feel this is due to very less difference in the value functions of hitting and sticking (can be seen from the graph), and can be attributed to outliers in the episodes.

## Method 2: Temporal-Difference Learning
