# Continous Control-DRL-Udacity Report
Udacity Deep Reinforcement Learning Nanodegree Program<br/>
P2-Continous Control <br/>


### Description
For this project, I will train an robotic arm to reach target locations in [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. 

<img src=https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/images/example_env.png />



### Goal
In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.


### States and actions
The states consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Environment
The used environment for Windows 64 : [one agent Reacher Environment](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)<br/>


### Solution
I have solved the project by Deep Deterministic Policy Gradients (DDPG) algorithm. The main used reference to solve this project is the udacity [DDPG exercises](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum). <br/>


You can find the solution by refering to [Training code](https://github.com/HadisAB/Continous-Control---DRL---Udacity/tree/master/Training%20Code) and using below clarification. <br/>

* I have trained the agent for some episodes and for some maximum number of time-steps in each episode.
* The training loop is composed of acting (selects the action) and learning (updates the weights to maximize value estimation) steps. 
* Then update the target Actor and Critic weights by the current weights of the local Actor and Critic networks.


**Continous Control.py**: This is the main script which shows the intersections between the environment and agent by using following functions. <br/>

**model.py** : This is neural model for Actor and Critic network. Each consisting two hidden layers with 128 hidden nodes. In these networks the actor does the policy approximation, and the critic does the value estimation. The activation functions in Actor and Critic are Relu/tanh and Relu/Linear, respectively.


**ddpg_agent.py** : This is a class of agents activites which make agent be trained. <br/>


**checkpoint_actor.pth**: This stores the trained weights of Actor. <br/>

**checkpoint_critic.pth**: This stores the trained weights. 

### used parameters
BUFFER_SIZE = int(1e5)   &nbsp; &nbsp; replay buffer size<br/>
BATCH_SIZE = 128         &nbsp; &nbsp; minibatch size<br/>
GAMMA = 0.99            &nbsp; &nbsp; discount factor<br/>
TAU = 1e-3              &nbsp; &nbsp; for soft update of target parameters<br/>
LR_ACTOR = 2e-4         &nbsp; &nbsp; learning rate for Actor<br/>
LR_CRITIC = 2e-4        &nbsp; &nbsp; learning rate for Critic<br/>

### Result

<img src="https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/images/scores.png" />


<img src="https://github.com/HadisAB/Continous-Control---DRL---Udacity/blob/master/images/scoretrend.png" />


### Ideas for future work
Here are some ideas for future work:

[Prioritized Experience Replay](https://arxiv.org/abs/1511.05952): 
> The idea behind using these technique for sampling from the replay buffer is that not all experiences are equal, some are more important than others in terms of reward, so naturally the agent should at least prioritize between the different experiences.


[Asynchronous Actor Critic](https://medium.com/emergent-future/simple-reinforcement-learning-with-tensorflow-part-8-asynchronous-actor-critic-agents-a3c-c88f72a5e9f2): 
> The idea is to have a global network and multiple agents who all interact with the environment separately and send their gradients to the global network for optimization in an asynchronous way.



