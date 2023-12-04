## Motivation
Matrix multiplication has been known as an NP-hard problem. in a longstanding research effort, matrix multiplication algorithms have been discovered by attacking this tensor decomposition problem using human search, continuous optimization, and combinatorial search. These approaches often rely on human-designed heuristics, which are probably suboptimal. Here the paper will introduce a new approach with deep reinforcement learning for solving the matrix multiplication problem. 

## Algorithm as tensor decomposition
A matrix multiplication is bilinear, it can be fully represented by a 3D tensor, which can be represented by the outer product of three vectors $__u__ $

## Terminologies
##### Exploration-Exploitation in RL: 
* The policy head helps the agent decide which action to take by sampling from the probability distribution. It introduces exploration as actions are selected with some randomness.
* The value head assists in the exploration-exploitation trade-off by providing an estimate of the expected value of being in the current state. This estimate guides the policy head to favor actions that are expected to lead to higher cumulative rewards.

