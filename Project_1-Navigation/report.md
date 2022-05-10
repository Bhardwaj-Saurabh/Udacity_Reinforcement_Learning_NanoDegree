# Project 1: Navigation

# Goal
Agent must collect as many yellow bananas as possible while avoiding blue bananas. In order to solve the enviornment, an average score of 13 over 100 episodes must be achieved by the agent.

# Enviornment
State space: 37 dimensions which has the agent's velocity, along with ray-based perception of objects around agent's forward direction. Action space: Four discrete actions are available as followings:

0 - move forward.
1 - move backward.
2 - turn left.
3 - turn right.
The task is defined as an episodic task.

## Description of the implementation

### Algorithms
In order to solve this challenge, I have used below mentioned deep reinforcement learning algorithms:

* [Deep Q-Network](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf)

##### Deep Q-Network
In a enviornment where state space is infinite or very large, creating and updating Q-table will not be efficient. This is where Deep Q Learning comes to rescue. In DQN, the Q values are estimated using a NN. See the image below for reference.

![](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_1-Navigation/results/DQN.jpg)  

At each time step, a tuple of state, action, reward, and new state (S, A, R, S_new) is recieved. This tuple is called an experience. These experience is in a sequencial order. To break this coorelation, a sample of small batch from the stroed experience called replay buffer is feed to the NN. Indeed, to find the best action, biggest Q-value from the output vector is selected. In the start, agent does not perform well, but that is OK. As training progress, agent start to learn better and better.

The error is calculated by taking the difference between Q target and Q values. Weight update is done by the following equation. 

![](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_1-Navigation/results/weightupdate.jpg)

There are two processes that are happening in this algorithm:

1. We sample the environment where we perform actions and store the observed experiences tuples in a replay memory.
2. Select the small batch of tuple random and learn from it using a gradient descent update step.

I have implemented the DQN as folloings.

Q-network architecture:

Input layer FC1: 37 nodes in, 64 nodes out
Hidden layer FC2: 64 nodes in, 64 nodes out
Hidden layer FC3: 64 nodes in, 64 nodes out
Output layer: 64 nodes in, 4 out — action size

### Hyperparameters
There were many hyperparameters involved in the experiment. The value of each of them is given below:

BUFFER_SIZE = int(1e5) # replay buffer size
BATCH_SIZE = 64 # mini batch size
GAMMA = 0.99 # discount factor
TAU = 1e-3 # for soft update of target parameters
LR = 5e-4 # learning rate
UPDATE_EVERY = 4 # how often to update the network
Epsilon start = 1.0
Epsilon start = 0.01
Epsilon decay = 0.995

## Plot of Rewards
This graph shows the rewards per episode within the training phase, as well as the moving mean.  
It illustrates that the Agent is able to receive an average reward of at least +13 over 100 episodes.  

In this case, the Agent solved the environment after **21 episodes**.

![](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_1-Navigation/results/Navigation.jpg)

## Conclusion
The environment was solved in 340 episodes with average score of 13. Indeed, there are improvement which can be made from here. Below are some ideas to improveme the results.
 
## Ideas for Future Work

Other algorithms proposed to enhance the performance of the Deep Q-Network. Future work could implement them to verify their performance in this environment. Those algorithms are:  
   * [A3C - Asynchronous advantage actor-critic](https://arxiv.org/abs/1602.01783)  
   * [Noisy DQN](https://arxiv.org/abs/1706.10295)  
   * [Distributional DQN](https://arxiv.org/abs/1707.06887)

## Credit

![source] https://www.freecodecamp.org/news/an-introduction-to-deep-q-learning-lets-play-doom-54d02d8017d8 
