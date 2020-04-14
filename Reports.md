# Continous Control-DRL-Udacity Report
Udacity Deep Reinforcement Learning Nanodegree Program<br/>
P2-Continous Control <br/>


### Description
For this project, I will train an agent to navigate (and collect bananas!) in a large, square world.<br/>
[Environment view](https://github.com/HadisAB/Navigation-DRL-Udacity/blob/master/images/videoexample.mp4)



### Goal
A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.<br/>
The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

### States and actions
The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. <br/> Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:<br/>

0 - move forward.<br/>
1 - move backward.<br/>
2 - turn left.<br/>
3 - turn right.

### Environment
The used environment for Windows 64 :
[Banan Envoronment](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)


### Solution
I have solved the project by Deep Q-Networks and also considering the 'Experience Replay' and 'Fixed Q Targets' to improvement the training. You can find the solution by refering to [training code](https://github.com/HadisAB/Navigation-DRL-Udacity/tree/master/Training%20code) and using below clarification. <br/>

**Navigation.py**: This is the main script which shows the intersections between the environment and agent by using following functions. <br/>

**model.py** : This is a neural network consists of two hidden layers with 64 nodes. I have also used Relu function as activation function.<br/>

**dqn_agent.py** : This is a class of agents activites which make agent be trained. <br/>
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
