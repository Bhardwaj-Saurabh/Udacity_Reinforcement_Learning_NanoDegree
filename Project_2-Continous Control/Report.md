# Project 2 - Report
## Continuous Control with DDPG agent

## Algorithm
To solve the enviornment, I have used Deep Deterministic Policy Gradient (DDPG) algorithm. It consists of two different neural networks mainly for value-based and policy based predictions. The detail of the algorithm can be found on the below mentioned paper.

Paper: [Lillicrap, Timothy P., et al. "Continuous control with deep reinforcement learning." arXiv preprint arXiv:1509.02971 (2015).](https://arxiv.org/abs/1509.02971)

Due to it's off-policy training nature, it can easily be used for continuous action spaces based enviornments.

#### Model Architecture

The actor (and the actor target) network uses 3 fully-connected layers:

- state_size -> 96 -> ReLU (activation)
- 96 -> 96 -> ReLU (activation)
- 96 -> action_size -> tanh (activation)

The critic (and the critic target) network uses 3 fully-connected layers:

-   state_size -> 96 -> ReLU (activation)
-   96 + action_size -> 96 -> ReLU (activation)
-   96 -> 1

To encourage exploration, the Ornstein -Uhlenbeck process as provided during lectures is used to add a little bit of noise to the actions. The noise is not added to the actions at evaluation time.

#### Hyperparameters
Below hyper-parameters were used to train the agent. 

- BUFFER_SIZE = int(1e5)  # replay buffer size
- BATCH_SIZE = 128        # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR_ACTOR = 1e-3         # learning rate of the actor 
- LR_CRITIC = 1e-3        # learning rate of the critic
- WEIGHT_DECAY = 0        # L2 weight decay


## Performance

The agents solved the environment in  **18**  episodes by reaching a collective average reward of 30.0 over last 100 episodes.

### Reward vs. Episode

The below graphs shows the rewards vs Episode after training is completed.

![reward](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_2-Continous%20Control/results/DDPG_result.jpg)

## Improvements
- Using prioritized experience replay which can certainly improved the performance in many cases.
- Other algorithms such as PPO also can perform better perticulary in continious action spaces.
- Optimize hyperparameters: particularly the actor and critic learning rates
- To reduce the noise, try to limit updated each timesteps which can help to make the training faster as well.
