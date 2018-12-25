Udacity - *Deep Reinforcement Learning Nanodegree* | ***Alexander Ekdahl***


# Project 2 - Continuous Control

This notebook showcase how to train 20 Unity ML-Agents to control double-jointed arms by moving them to target locations. 


![Unity Environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/images/reacher.png "Unity Environment")

### 1. Problem statement and approach
Essentialy, the agent needs to learn how to control a double-jointd arm to stay as close to the target loacation as possible for as many timesteps as possible. The agent does this by setting four continouos values in an action vector that control the torque of the arm joints. The goal for the agent is then to simply figure out how to end up with as high reward as possible. The problem is considered solved when the agent (in this case the average of 20 agents) achieves +30 points across 100 consequtive runs in the environment.

We are training the agents on 1000 episodes with a maximum of 1000 iterations (timesteps) in each episode. The aim is to reach +30 points to solve the environment. The training will stop when the environment is solved.

### 2. Environment
- Number of agents: 20
- Number of states: 33
- Number of possible actions: 4 
    - *Corresponding to the torque of the double-jointed arm*
- Rewards: 
    - Correct location per timestep: +0.1

### 3. Learning Model
The model is a Deep Neural Network with 3 fully connected layers. It takes the 33 different states from the state vector as input, and outputs the action represented by a vector containing four continouos values. 
- Input: state_size (33), Output: 400
- Input: 400, Output: 300
- Input: 300, Output: action_size (1)

Model Parameters:
- Replay buffer size: 1.000.000
- Minimum batch size: 128
- Discount factor: 0.99
- Soft update of target: 0.001
- Learning Rate Critic: 0.001
- Learning Rate Actor: 0.001
- Weight decay of critic: 0

Agent Parameters:
- Episodes: 1000
- Maximum timesteps: 1000
- Learning intervals: 20
- Learning times: 10

### 4. Result
As the below results show, the model was able to solve the environment after 600 iterations (episodes) but was able to further improve performance until it kind of evens out around 1000 episodes or so. The maximum score achieved was 16.70 across 100 consecutive iterations.

|           |            |
| :-------------: |:-------------:|
| ![Results graph](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img2.png "Results graph")  | ![Results table](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img3.png "Results table") |

### 5. Next steps

- Improving the results by tweaking the many static variables set in this model could be a next step to take to simply try out different settings. 
- From there, it seem that some of the addons to the DQN algorithm can be used to further improve the performance. Trying out Double DQN, Prioritized Experience Replay or Dueling DQN might be a good idea.
- In this model we did not use the images produced by the video game as learning input to the model. Using the pixels of the images with CNN layers may also improve the results. Quite possibly with a trade off on computational performance and cost though.
