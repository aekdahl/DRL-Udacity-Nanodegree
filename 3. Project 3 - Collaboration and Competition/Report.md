Udacity - *Deep Reinforcement Learning Nanodegree* | ***Alexander Ekdahl***


# Project 3 - Collaboration and Competition

This notebook showcase how to train two competing Unity ML-Agents to play a "slightly" modified version of tennis. Modified, in such way that the main aim is to get the ball over the net as many times as possible, instead of making the opponent miss the ball as in regular tennis. This also introduce an element of collaboration while competing.


![Unity Environment](https://github.com/Unity-Technologies/ml-agents/raw/master/docs/images/tennis.png "Unity Environment")

### 1. Problem statement and approach
Essentialy, each agent needs to learn how to keep the ball from touching the ground and to hit it back to the opponents side (staying within bounds). The agents does this by providing an action vector in each state (timestep) corresponding to movement and jumping, and gets rewarded +0.1 when it manage to hit the ball over the net, and -0.01 failing to do so, and letting the ball hit the ground. The environment is considered solved, when the average (over 100 episodes) of the scores is at least +0.5. The task is episodic, and the score of each episode is derived by taking the maximum score of the two agents. Hence, one of the agents needs to succeed with hitting the ball over the net a minimum of 5 times per episode over 100 episodes to solve the environment.

We are training the agent on 2000 episodes with a maximum of 1000 iterations (timesteps) in each episode. The aim is to reach +0.5 points to solve the environment, at which point we will abort the training and present the result.

### 2. Environment
- Number of agents: 2
- Number of states variables: 24
- Number of possible actions: 2 
    - *Movement forward/Backward*
    - *Movement jump*
- Rewards: 
    - Hitting the ball over the net: +0.1 
    - Letting the ball touch the ground or hit it out of bounds: -0.01

### 3. Learning Model
The model is a Deep Neural Network with 3 fully connected layers. It takes the 24 different state variables from the state vector as input, and outputs an action vector containing 2 continous values to control the racket. 

***Actor***
- Input: state_size (24), Output: 254
- Input: 254 (Batch normalized), Output: 128
- Input: 128, Output: action_size (2)

***Critic***
- Input: state_size (24), Output: 254
- Input: 254 (Batch normalized), Output: 128
- Input: 128, Output: action_size (2)

Model Parameters:
- Replay buffer size: 1.000.000
- Minimum batch size: 128
- Discount factor: 0.99
- Soft update of target: 0.001
- Learning Rate Critic: 0.001
- Learning Rate Actor: 0.001
- Weight decay of critic: 0
- Learning intervals: 2
- Learning times: 10

Agent Parameters:
- Episodes: 2000
- Maximum timesteps: 1000

As a basis of my work in this project, I used the model built in the second project on continuous control. A DDPG, or a Deep Deterministic Policy Gradient Algorithm with gradient clipping to avoid too high gradients and batch normalization to ensure interpretation of values across multiple environments and episodes for training. As with the DQN model in project 1, this model also use experience replay buffer to collect and sample the data used for training the algorithm. Starting from that, I adjusted the code to cater for a 2 agent setup. At last, I updated the layers of the neural net for a smaller set of state variables (24).

### 4. Result
As the below results show, the model was able to solve the environment after 335 episodes. The maximum score achieved was 0.5 across 100 consecutive iterations (after which the training was aborted).

|           |            |
| :-------------: |:-------------:|
| ![Results graph](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/3.%20Project%203%20-%20Collaboration%20and%20Competition/BA7A1105-2A4B-4A2F-B607-7CCFF56DC455.png "Results graph")  | ![Results table](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/3.%20Project%203%20-%20Collaboration%20and%20Competition/1171458A-CA0D-44DE-BC5C-28DCB7F0F530.png "Results table") |

### 5. Next steps
- Improving the results by tweaking the many static variables set in this model could be a next step to take to simply try out different settings. 
- Further, Prioritized Experience Replay can be a good idea since we use an experience replay buffert.
- Last, I decided to use a DDPG model, however, there are other possible models to use such as PPO or TRPO that could be a better fit for the challenge.
