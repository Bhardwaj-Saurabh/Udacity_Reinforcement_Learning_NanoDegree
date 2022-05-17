# Project 2 - Continuous Control with DDPG agent
This folder contains the solution to project 2 on continous control for the [Udacity Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893).

In this project a double-jointed arm is trained to reach target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.

The details of step-by-step implementation is available in [**Report.md**](Report.md).

## Project Details

### Goal
The goal of this project is to create and train a double-jointed arm agent that is able to maintain its hand in contact with a moving target for as many time steps as possible. The environment is considered solved, when the average (over last 100 episodes) of those average scores is at least +30.

### Environment
This environment has been built using the **Unity Machine Learning Agents Toolkit (ML-Agents)**, which is an open-source Unity plugin that enables games and simulations to serve as environments for training intelligent agents. You can read more about ML-Agents by perusing this [GitHub repository](https://github.com/Unity-Technologies/ml-agents). The enviornment provided in the project is similar to the Reacher enviornment. 

![Recher Enviornment](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_2-Continous%20Control/results/reacher.gif)

The observation space consists of 33 variables corresponding to 
- position, 
- rotation, 
- velocity, 
- angular velocities of the arm. 

Each action is a vector with four numbers, corresponding to **torque applicable to two joints**. Every entry in the action vector should be **a number between -1 and 1**.

For this project, two separate versions of the *Reacher* Unity environment are provided:
* Version 1: The first version contains a single agent
The task is episodic, and the environment is considered solved when the agent gets an average score of +30 over 100 consecutive episodes.

* Version 2: The second version contains 20 identical agents, each with its own copy of the environment  
The barrier for solving the second version of the environment is slightly different, to take into account the presence of many agents. In particular, your agents must get an average score of +30 (over 100 consecutive episodes, and over all agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 20 (potentially different) scores. We then take the average of these 20 scores.
- This yields an average score for each episode (where the average is over all 20 agents).

## Getting Started
### Included in this repository

* The code used to create and train the Agent
  * Continuous_Control.ipynb
  * ddpg_agent.py
  * model.py
  
* The trained model
  * checkpoint_actor.pth
  * checkpoint_critic.pth
  
* A file describing all the packages required to set up the environment
  * python folder
  
* A Report.md file explaining the step-by-step process and the learning algorithm. In addition, some ideas to improve the results have been presented in the report.

* README.md File

### Installation

Installing PyTorch
* PyTorch 0.4.x install from https://pytorch.org or https://pytorch.org/get-started/previous-versions/

It is recommended to install other dependencies through **Anconda**: https://anaconda.org/
* Python 3.6
* pickle
* numpy
* tensorboardx: tensorboardX is used for saving data to visualise the training process from PyTorch to tensorboard 

To create an Anaconda virtual environment for Python it is recommended to follow the guildelines at the Anaconda website. In general you would want to do the following in the terminal:

**Linux and Mac:**

    $ conda create --name drlnd python=3.6
    $ source activate drlnd

**Windows**

    $ conda create --name drlnd python=3.6
    $ activate drlnd

The unity environment needed for this assignment can be found in the folder **/unity-ml-agents/**. Here you will find environments for Mac, Linux, and Windows.

### Running the code

**Training the agent**

Before training the agent, hyper-parameters can be set in **ddpg_agent.py**. If you want to experiment with the neural networks architecture for the actor and critic, it can be found in **model.py**. 

To start training the agent run the following command:

    $ jupyter notebook
    
Navigate to the root of the project in your system and click on the `Continuous_Control.ipynb` notebook. 

tensorboard can be used to visualise the training process (mean reward) in your browser. Start tensprboard by running the following command:

    $ tensorboard --logdir runs

When training is done, the best model weights are saved as **checkpoint_actor.pth** and **checkpoint_critic.pth**.

## Results

Below are the final results from Version 2 of the environment.

Detailed results are found in [**Report.md**](Report.md).

### Version 2: 20 agents
![training_results](https://github.com/Bhardwaj-Saurabh/Udacity_Reinforcement_Learning_NanoDegree/blob/main/Project_2-Continous%20Control/results/DDPG_result.jpg)

## Acknowledgement
Some parts of the codes are taken from the DDPG lesson in Udacity Reinforcement Learning Nano-Degree - part 2. 

## License
GPL-3.0

## Author
Saurabh Bhardwaj
