This report presents a solution to the Continuous Control Project in the Udacity Deep Reinforcement Learning Nanodegree. 

## Overview

In the Udacity Banana environment, a vehicle can move in any of the cardinal directions to obtain a banana. The vehicle receives a positive reward for reaching a yellow banana and a negative reward for a blue banana. The [state space](https://github.com/Unity-Technologies/ml-agents/issues/1134) includes both the forward and lateral velocities and the relative angular position of both types of bananas. An episode represents 1000 actions. To solve this environment, the user must attain an average score of +13 over 100 episodes.

This repository presents a solution in 489 episodes using a Deep Q-Network. The code is adapted from a Udacity-supplied solution to the OpenAI gym-Lunar Lander environment. The network trains in 4 min. 19 s. using an Intel i9-9900K 8-core cpu, 64 GB of RAM, and an 11GB NVIDIA 2080 TI GPU. Fig. 1 depicts the vehicle collecting a yellow banana. A video can be seen here. Fig. 2 shows the score stochastically increasing as the model trains.


## Deep Q-Network Approach
Mnih et. al. introduced DQN's in Nature in 2015 (update sentence). Given a state s, a Deep Q-Network (DQN) estimates the action a that maximizes the expected discounted reward. A deep neural network maps states to actions. For training, experiences are buffered, randomized, and batched together. During training, actions are chosen using an epsilon-greedy strategy, with epsilon decrementing after each episode.

### Network Architecture and Hyperparameters
The input to the architecture is a 37-element state vector. The architecture of the network consists of a 37 x 64 fully-connected layer, a relu activation function, a 64 x 64 fully connected layer, a second relu activation function, and a 64 x 4 fully connected layer. The output is a four-element action vector that  represents the cardinal directions. For a trained network, the output with the highest value is the action associated with the input state.

Key hyperparameters that represent the network include batch size (64), learning rate (1e-3), discount factor (0.99), buffer size (1e5), and tau (1e-3). During an episode of training, the weights of the network are updated. These weights and the weights at the beginning of the episode are added together by the ratio of tau:(1 - tau). (double-check).

### Hyper-parameter Tuning

The hyperparameters were tuned individually to solve the environment in fewer episodes. The initial learning rate was 5e-4, and the initial values of the other parameters are the same as their current values.

Increasing the batch size from 64 to 128 to 256 increased the training time (from  to 305 s. to 356 s). 

The batch size was reset to 64, and the learning rate was increased to 5e-3. This rate was too high for learning, and it was then reduced to 1e-3. Setting gamma to 1 and later 0.95 marginally increased the number of episodes needed to train (511 and 513 respectively), and the value was returned to 0.99. 
 	
Changing the value of tau dramatically reduced performance. Increasing tau to 1e-2 produced a solution in 819 episodes, whereas decreasing tau to 1e-4 yielded an average score of less than 5 after 500 episodes.

Varying the buffer size to 1e6 and later 1e4 resulted in a solution in 556 and 551 episodes respectively.

These observations suggest that the two most sensitive hyperparameters are the learning rate and tau.

In addition, the number of weights in the network did not significantly affect training. Modifying the size of the second fully-connected layer to 32 x 32 and later 128 x 128 (with the adjacent fc layers adjusted accordingly) resulted in only a modest increase in the number of episodes needed to train the network (492 and 512 respectively).

## Future Work

To be sure, the agent's performance may be improved with a finer grid search. 
	
One area of future exploration includes training with pixels as input, and another area of exploration is the general applicability of hyper-parameters. In Mnih, the same set of hyper-parameters and a similar network architecture were used across a varigated set of Atari environments with pixelated input. Here, the same set of hyper-parameters and a similar network architecture successfully solved both the unpixelated Lunar-Lander and unpixelated Banana environments. Thus, the hyper-parameters and the network architecture used in Mnih. may solve the pixelated Banana environment.

