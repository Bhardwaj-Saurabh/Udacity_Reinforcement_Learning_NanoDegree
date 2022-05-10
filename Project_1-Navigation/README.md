[//]: # (Image References)

[random_gif]: https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_1-Navigation/results/random_agent.gif
[DQN_result]: https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_1-Navigation/results/Navigation.jpg

# Project 1: Navigation

### Introduction

In the navigation project, I train an agent to navigate and collect bananas in a large, square world using Univy Enviornment.


Random agent             
:-------------------------:
[Random Agent][random_gif] 


Reward for collecting a yellow banana: +1
Reward for collecting a blue banana: -1 

### Goal

Agent must collect as many yellow bananas as possible while avoiding blue bananas. In order to solve the enviornment, an average score of 13 over 100 episodes must be achieved by the agent.

### Enviornment

State space: 37 dimensions which has the agent's velocity, along with ray-based perception of objects around agent's forward direction.
Action space: Four discrete actions are available as followings:

- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The task is defined as an episodic task.

### Getting Started

1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

2. Place the file in this folder, unzip (or decompress) the file and then write the correct path in the argument for creating the environment under the notebook `Navigation_solution.ipynb`:

```python
env = env = UnityEnvironment(file_name="Banana.app")
```

### Description

- `dqn_agent.py`: code for the agent used in the environment
- `model.py`: code containing the Q-Network used as the function approximator by the agent
- `checkpoint.pth`: saved model weights for the original DQN model
- `Navigation.ipynb`: notebook containing the solution


### Instructions

Follow the instructions in `Navigation.ipynb` for training your an agent! 

To watch a trained smart agent, please see the instructions below:

- **DQN**: If you want to run the original DQN algorithm, use the checkpoint `dqn.pth` for loading the trained model. Also, choose the parameter `qnetwork` as `QNetwork` while defining the agent and the parameter `update_type` as `dqn`.


### Enhancements

Several enhancements to the original DQN algorithm have also been discussed in the udacity nano degree program. Related papers as below:

- Double DQN [[Paper](https://arxiv.org/abs/1509.06461)] 
- Prioritized Experience Replay [[Paper](https://arxiv.org/abs/1511.05952)] 
- Dueling DQN [[Paper](https://arxiv.org/abs/1511.06581)] 

### Results

Plot showing the score per episode over all the episodes. The environment was solved in **340** episodes with average score of 13.

| Double DQN |

[dqn-scores] [DQN_result]


### Extra Challenge: Learning from Pixels

In the project, your agent learned from information such as its velocity, along with ray-based perception of objects around its forward direction.  A more challenging task would be to learn directly from pixels!

To solve this harder task, you'll need to download a new Unity environment.  This environment is almost identical to the project environment, where the only difference is that the state is an 84 x 84 RGB image, corresponding to the agent's first-person view.  (**Note**: Udacity students should not submit a project with this new environment.)

You need only select the environment that matches your operating system:
- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/VisualBanana_Windows_x86_64.zip)

Then, place the file in this folder, and unzip (or decompress) the file.  Next, open `Navigation_Pixels.ipynb` and follow the instructions to learn how to use the Python API to control the agent.

(_For AWS_) If you'd like to train the agent on AWS, you must follow the instructions to [set up X Server](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above.

### Dependencies

Use the `requirements.txt` file (in the [main](https://github.com/dalmia/udacity-deep-reinforcement-learning) folder) to install the required dependencies via `pip`.

```
pip install -r requirements.txt
```
