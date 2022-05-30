# Project 3 - Report
## Collaboration and Competition with DDPG agent

## Algorithm
To solve the enviornment, I have used Deep Deterministic Policy Gradient (DDPG) algorithm. It consists of two different neural networks mainly for value-based and policy based predictions. To train the multiple agents with shared memory, I have used the extended version of DDPG know MADDPG. The detail of the algorithm can be found on the below mentioned paper.

Paper: [Lowe, Ryan, et al. "Multi-agent actor-critic for mixed cooperative-competitive environments." Advances in Neural Information Processing Systems. 2017.](https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf)

Due to it's off-policy training nature, it can easily be used for continuous action spaces based enviornments. In this implementation, I have made use of fixed target and experience replay memory which helps the agent train with reduce noise or variance hence provide better generalized policy.

#### Model Architecture

The actor (and the actor target) network uses 3 fully-connected layers:
It is important to note that batchnormalization was applied to first and second layer. 

- state_size -> 256 -> batch_norm -> ReLU (activation)
- 256 -> 256 -> batch_norm -> ReLU (activation)
- 256 -> action_size -> tanh (activation)

The critic (and the critic target) network uses 3 fully-connected layers:
Batchnormalization was applied to only first.

- state_size -> 256 -> batch_norm -> ReLU (activation)
- 256 + action_size -> 256 -> ReLU (activation)
- 256 -> 1

To encourage exploration, the Ornstein -Uhlenbeck process as provided during lectures is used to add a little bit of noise to the actions. The noise is not added to the actions at evaluation time.

#### Hyperparameters
Below hyper-parameters were used to train the agent. 

- BUFFER_SIZE = int(1e6)  # replay buffer size
- BATCH_SIZE = 128        # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR_ACTOR = 1e-4         # learning rate of the actor 
- LR_CRITIC = 1e-4        # learning rate of the critic
- WEIGHT_DECAY = 0        # L2 weight decay

## Performance

The agents solved the environment in  **1151** episodes by collective average reward of 0.50 over last 100 episodes. The target limit of training was set to 2000 episodes.

### Reward vs. Episode

The below graphs shows the rewards vs Episode after training is completed.

![results](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_3-Collaboration%20and%20Competition/images/final_result.png)

## Improvements
- Using prioritized experience replay which can certainly improved the performance in many cases.
- Other algorithms such as TRPO and PPO also can perform better perticulary in continious action spaces.
- Optimize hyperparameters: particularly the actor and critic learning rates
- To reduce the noise, try to limit updated each timesteps which can help to make the training faster as well.
