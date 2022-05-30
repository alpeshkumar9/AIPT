# AIPT Project: Tower of Hanoi

**Goal:** You will reflect upon the search algorithms learned during the lectures and implement two of them to solve the Tower of Hanoi.

![Tower of Hanoi](https://user-images.githubusercontent.com/8064993/171058046-ce4f1c57-e2fc-4b53-afb8-05ffadc57f46.png)

**Setting of the game:**
- The Tower of Hanoi is a puzzle game with usually 3 pegs and a fixed number of disks. For this project, we will use 4 pegs. Consider n > 0 number of discs.
- Initial state: At the start, all the disks are in the leftmost peg, with the largest disk on the bottom and the smallest on the top.
- Goal state: All disks are moved over to the rightmost peg.

**Rules of the game:**
- You can only move one disk to any other peg in each move, and you can only move the top disk on a peg.
- The top disk of any peg can be moved to the top disk of any other peg, with the restriction that you cannot move a larger disk on top of a smaller disk (i.e., disks can only be moved to empty pegs or on top of larger disks).
- This is a unit-cost domain, all moves cost the same. Path cost is its length.


1) Rationale behind the representation you have chosen for the problem.
    - For building tower of Hanoi in Python language, we have used “Lists”, which are built-in data structures in Python. Furthermore, “Lists” provides the option to store create any number of list in a “Lists” and also follows FIFO technology which we found to be very useful in order to solve problem.

    - The algorithm developed has been coded using functional structures. The general purpose of each function is described in upcoming points.

    - The 4-peg Towers of Hanoi problem has many different pair of states, even states are duplicated during traversing process. For example, if we move disk from peg A to peg B, and then another disk from peg C to peg D, then repeating these 2 moves in reverse order will also generate the same state. Hence, there are chances of duplication of states.

    - The two searching algorithms we studied in lab were DFS & BFS.

    - DFS generates every path to a given depth hence it is unable to detect the duplication. The optimal DFS solution for 6-disk 4-peg TOH problem is 17 moves. Thus, a brute-force DFS would generate about 3.7!" ≈ 6 × 10^9 nodes

    - However, BFS does not expend beyond the unique states because for any n-disk problem there are only 4^n states. Thus, for 6-discs, there are only 4^6 = 4096 states.

    - **Hence, we choose BFS as it is more efficient than DFS.**

2) Search algorithms chosen to solve the problem

    - We have used Breadth First Search (BFS) algorithm which is a recursive algorithm, to solve this problem

    - Starting from initial state, BFS traverse every possible sub-state at level n before moving to next level n+1, so same state is never visited. Thus, the purpose of this search algorithm is to visit all the states while avoiding cycles.

    - The algorithm then takes the next state from already visited sub-states, going from older ones towards the newer ones. At each state, it performs following tasks:
      (a) Follow one by one of sub-states at each parent state 
      (b) Look for unvisited state
      (c) Mark the parent state as visited and
    - The algorithm moves to next level n+1 only when it finishes expanding at current level n. This way a queue is formed in which the first element enters the queue is also the first element that leaves the queue (FIFO)

3) Two heuristics devised for the problem and experimental evidence (graphs or tables) to assess which heuristic makes the algorithm more efficient in solving the problem.

    - The 2 heuristics used are **Breadth First Search and BestFS**
    - In Bread First Search heuristic function,
      * admissible_heuristic function is main which hold code for BFS.
      * Algorithm visit each state to calculate the heuristic value, h(n) using heuristic_evaluation function. As it scan each states before moving along a particular path it helps in avoiding duplication.
      * Function create POSSIBLE MOVE of parent node from list, A* star algorithm based on g(n) & h(n) values selects the POSSIBLE MOVE with minimum cost values and make It as parent node.
      * This steps are repeated until the “initial state” and “final state” are not equal.
      * back_tracing function gives the optimal steps to go to the final state.
      
    - In BestFS heuristic function,
      * A_STAR function is main which hold code for BestFS.
      * Algorithm visit each state to calculate the heuristic value, h(n) using heuristic_evaluation function. H(n) is calculated only when the disc in the final peg. That is why BestFS is also called as greedy algorithm.
      * Function create POSSIBLE MOVE of parent node from list, A* star algorithm based on g(n) & h(n) values selects the POSSIBLE MOVE with minimum cost values and make It as parent node.
      * This steps are repeated until the “initial state” and “final state” are not equal.
      * back_tracing function gives the optimal steps to go to the final state.
