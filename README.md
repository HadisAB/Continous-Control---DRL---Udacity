# Continous-Control---DRL---Udacity
P2-Continous Control- Udacity Deep Reinforcement Learning Nanodegree Program


## Project details
For this project, I will train an robotic arm to reach target locations in [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. 

<img src=https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/images/example_env.png />


### Goal
In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.


### States and actions
The states consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

## Getting Started

1. Download [Anaconda](https://www.anaconda.com/distribution/) and install it.
2. Run the 'anaconda prompt' and use below commands to creat an environment and install python 3.6
> conda create --name drlnd python=3.6 <br/>
> activate drlnd 
3. Open anaconda navigator, select drland in the anaconda environments, install and launch spyder. I have used spyder to run my codes. You may use another interface. 
4. I have used Unity's rich environments to train and design the algorithms.<br/>
Download the used environment for Windows 64 :
[one agent Reacher Environment](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)<br/>
5. Install [unity ml-agents](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md), [numpy](https://numpy.org/) and [pytorch](https://pytorch.org/) through shown links.
6. Install matplotlib.pyplot by using below command in 'anaconda prompt':<br/>
> pip install matplotlib.pyplot



## Instructions
I have solved the project by Deep Deterministic Policy Gradients (DDPG) algorithm. The main used reference to solve this project is the udacity [DDPG exercises](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum). <br/>

Follow below steps to run the code:
1. Install all required dependencies of the project based on above links.
2. Download the [ddpg-agent.py](https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/Training%20Code/ddpg_agent.py), [model.py](https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/Training%20Code/model.py) and [Continous Control.py](https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/Training%20Code/Continuous%20Control.py) files from [Training code](https://github.com/HadisAB/Continous-Control---DRL---Udacity/tree/master/Training%20Code).
3. Put all the downloded .py files in one folder.
4. Open the [Continous Control.py](https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/Training%20Code/Continuous%20Control.py) in spyder and Run the code.


Also refer to the [report](https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/Report.md) for more clarification of the method. 


