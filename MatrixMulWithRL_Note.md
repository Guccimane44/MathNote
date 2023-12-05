## Motivation
Matrix multiplication has been known as an NP-hard problem. in a longstanding research effort, matrix multiplication algorithms have been discovered by attacking this tensor decomposition problem using human search, continuous optimization, and combinatorial search. These approaches often rely on human-designed heuristics, which are probably suboptimal. Here we will focus on practical matrix multiplication algorithms, which correspond to explicit low-rank decompositions of the matrix multiplication tensor. The paper will introduce a new approach with deep reinforcement learning for picking the best matrix multiplication algorithm, which includes __Strassen's__, __Laderman's__, __Hopcroft and Kerr's__, and many undiscovered algorithms.

## Algorithm as tensor decomposition
A matrix multiplication is bilinear, it can be fully represented by a 3D tensor, which can be represented by the outer product of three vectors $u$, $v$, $w$. (See the formula)
We write Tn for the tensor describing n × n matrix multiplication. The tensor Tn is fixed 
(that is, it is independent of the matrices to be multiplied), has entries in {0, 1}, and is of size n2×n2×n2. If a tensor T can be decomposed into R rank-one terms, we say the rank of T is at most R, or Rank (T) ≤ R. An example can be seen in the figure 1: we end up getting Strassen’s algorithm with R=7. 

## DRL for algorithm discovery
Big idea short: we modeling the environment as a single player game: TensorGame. The game state after step t is described by a tensor St, which is initially set to the target tensor we wish to decompose: S0 = Tn. In each step t of the game, the player 
selects a triplet (u(t), v(t), w(t)), and the tensor St is updated by subtracting the resulting rank-one tensor: 

$$\mathcal{S_t} \leftarrow \mathcal{S_\left(t-1\right)} − \mathbf{u^\left(t\right)} \otimes \mathbf{v^\left(t\right)} \otimes \mathbf{w^\left(t\right)} $$

The goal of the player is to reach the zero tensor St = 0 by applying the smallest number of moves. When the player reaches the zero tensor, the sequence of selected factors satisfies
$$\mathcal{T_n} = \sum_{t=1}^R \mathbf{u^\left(t\right)} \otimes \mathbf{v^\left(t\right)} \otimes \mathbf{w^\left(t\right)} $$
(where R denotes the number of moves), which guarantees the correctness of the resulting matrix multiplication algorithm. To avoid playing unnecessarily long games, we limit the number of steps to a maximum value, $R_{limit}$.

To play TensorGame, we propose AlphaTensor, an agent based on AlphaZero1, which achieved tabula rasa superhuman performance in the classical board games of Go, chess and shogi, and on its extension to handle large action spaces Sampled AlphaZero. Similarly to AlphaZero, AlphaTensor uses a deep neural network to guide a Monte Carlo tree search (MCTS) planning procedure. The network takes as input a state (that is, a tensor St to decompose), and outputs a policy and a value. The policy provides a distribution over potential actions. As the set of potential actions (u(t), v(t), w(t)) in each step is enormous, we rely on sampling actions rather than enumerating them21,22. The value provides an estimate of the distribution z of returns (cumulative reward) starting from the current state St. With the above reward scheme, the distribution z models the agent’s belief about the rank of the tensor St. To play a game, AlphaTensor starts from the target tensor (Tn) and uses the MCTS planner at each step to choose the next action. Finished games are used as feedback to the network to improve the network parameters.

## Algorithm discovery results
The results are impressive: AlphaTensor re-discovers the best algorithms known for multiplying matrices. More importantly, AlphaTensor improves over the best algorithms known for several matrix sizes. AlphaTensor generates a large database of matrix multiplication algorithms—up to thousands of algorithms for each size. We exploit this rich space of algorithms by combining them recursively, with the aim of decomposing larger matrix multiplication tensors. Using this approach, we improve the state-of-the-art results for more than 70 matrix multiplication tensors. A crucial aspect of AlphaTensor is its ability to learn to transfer knowledge between targets (despite providing no prior knowledge on their relationship). By training one agent to decompose various tensors, AlphaTensor shares learned strategies among these, thereby improving the overall performance (see Supplementary Information for analysis). Finally, it is noted that AlphaTensor scales beyond current computational approaches for decomposing tensors.
* From a mathematical standpoint, the diverse algorithms discovered by AlphaTensor show that the space is richer than previously known. AlphaTensor finds more than 14,000 non-equivalent factorizations (with standard arithmetic) that depart from this scheme, and have different properties (such as matrix ranks and sparsity—see 
Supplementary Information).
* Tensors can represent any bilinear operation, such as structured matrix multiplication, polynomial multiplication or more custom bilinear operations used in machine learning.
* We show a use-case where AlphaTensor finds practically efficient matrix multiplication algorithms, tailored to specific hardware, with zero prior hardware knowledge. Although the discovered algorithm has the same theoretical complexity as Strassen-square, it outperforms it in practice, as it is optimized for the considered hardware.

## Terminologies
##### Exploration-Exploitation in RL: 
* The policy head helps the agent decide which action to take by sampling from the probability distribution. It introduces exploration as actions are selected with some randomness.
* The value head assists in the exploration-exploitation trade-off by providing an estimate of the expected value of being in the current state. This estimate guides the policy head to favor actions that are expected to lead to higher cumulative rewards.

