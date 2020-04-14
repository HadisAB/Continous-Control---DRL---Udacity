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


You can find the solution by refering to [training code](https://github.com/HadisAB/Navigation-DRL-Udacity/tree/master/Training%20code) and using below clarification. <br/>

**Continous Control.py**: This is the main script which shows the intersections between the environment and agent by using following functions. <br/>

**model.py** : This is neural model for Actor and Critic network. Each consisting two hidden layers with 128 hidden nodes. In these networks the actor does the policy approximation, and the critic does the value estimation. The activation functions in Actor and Critic are Relu/tanh and Relu/Linear, respectively.


**ddpg_agent.py** : This is a class of agents activites which make agent be trained. <br/>
In this part, the agent will take samples in RelayBuffer and also will be trained for each 4 steps. Consider below used functions for more details:<br/>

**Agent class**: <br/>
> * step() : It stores a step taken by the agent in the Replay Buffer. Then the agent will be learnt Every 4 steps.
> * act(): This returns actions for the given state based on an Epsilon-greedy.
> * learn(): This update the Neural Network value parameters.
> * soft_update(): It updates the value from the target Neural Network from the local network weights (That's part of the Fixed Q Targets technique).

**ReplayBuffer class**:<br/>
It implements a fixed-size buffer to store experience tuples (state, action, reward, next_state, done)
> * add(): It appends the samples to the memory
> * sample(): It randomly samples a batch of experience steps in the memory.

**model_weights.pth**: This stores the trained weights. 

### used parameters
BUFFER_SIZE = int(1e5)   &nbsp; &nbsp; replay buffer size<br/>
BATCH_SIZE = 64         &nbsp; &nbsp; minibatch size<br/>
GAMMA = 0.99            &nbsp; &nbsp; discount factor<br/>
TAU = 1e-3              &nbsp; &nbsp; for soft update of target parameters<br/>
LR = 5e-4               &nbsp; &nbsp; learning rate <br/>
UPDATE_EVERY = 4        &nbsp; &nbsp; how often to update the network

### Result

<img src="https://github.com/HadisAB/Navigation-DRL-Udacity/blob/master/images/scores.png" />


<img src="https://github.com/HadisAB/Navigation-DRL-Udacity/blob/master/images/scoretrend.png" />


### Ideas for future work

As discussed in the Udacity Course, a further evolution to this project would be to train the agent directly from the environment's observed raw pixels instead of using the environment's internal states (37 dimensions).
