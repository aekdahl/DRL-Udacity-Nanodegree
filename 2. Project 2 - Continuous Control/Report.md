Udacity - *Deep Reinforcement Learning Nanodegree* | ***Alexander Ekdahl***


# Project 2 - Continuous Control

This notebook showcase how to train 20 Unity ML-Agents to control double-jointed arms by moving them to target locations. 


![Unity Environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/images/reacher.png "Unity Environment")

### 1. Problem statement and approach
Essentialy, the agent needs to learn how to control a double-jointed arm to stay as close to the target loacation as possible for as many timesteps as possible. The agent does this by setting four continouos values in an action vector that control the torque of the arm joints. The goal for the agent is then to simply figure out how to end up with as high reward as possible. The problem is considered solved when the agent (in this case the average of 20 agents) achieves +30 points across 100 consequtive runs in the environment.

We are training the agents on 1000 episodes with a maximum of 1000 iterations (timesteps) in each episode. The aim is to reach +30 points to solve the environment. The training will stop when the environment is solved.

### 2. Environment
- Number of agents: 20
- Number of states: 33
- Number of possible actions: 4 
    - *Corresponding to the torque of the double-jointed arm*
    - *each action value are clipped to stay within the -1,1 boundary*
- Rewards: 
    - Correct location per timestep: +0.1

### 3. Learning Model
The model is a Deep Neural Network with 3 fully connected layers. It takes the 33 different states from the state vector as input, and outputs the action represented by a vector containing four continouos values. 

***Actor***
- Input: state_size (33), Output: 400
- Input: 400 (Batch normalized), Output: 300
- Input: 300, Output: action_size (4)

***Critic***
- Input: state_size (33), Output: 400
- Input: 400 (Batch normalized), Output: 300
- Input: 300, Output: action_size (4)

Model Parameters:
- Replay buffer size: 1.000.000
- Minimum batch size: 128
- Discount factor: 0.99
- Soft update of target: 0.001
- Learning Rate Critic: 0.001
- Learning Rate Actor: 0.001
- Weight decay of critic: 0
- Learning intervals: 20
- Learning times: 10

Agent Parameters:
- Episodes: 1000
- Maximum timesteps: 1000

Deep Deterministic Policy Gradient (DDPG):
As indicated in the project information pages, I set out to use the DDPG algorithm to solve the task. I started from the DDPG model implemented in the Pendulum example at Udacity and expanded on it to utilize multiple agents (20). Initially, the learning was disapointing and it was very hard to get any decent scores using only this modified version of the pendulum implementation. Two further tweaks made major improvements to the model, 1) Gradient clipping and 2) Batch normalization.

The gradient clipping made the model more reliable by avoiding too large gradients, and thereby weights, preventing the model from learning properly. Implementing the clipping as hinted in the projects benchmark implementation using torch.nn.utils.clip_grad_norm_(self.critic_local.parameters(), 1) on the critic introduced an upper limit of the gradients that improved the learning of the algorithm.

The Batch nomarlization of the input data to the network improved the learning somewhat similar to the gradient clipping as it ensured the inbound values from each episode and environment was properly scaled, and thereby comparable across each learning event.

### 4. Result
As the below results show, the model was able to solve the environment after 500 episodes. The maximum score achieved was 30.01 across 100 consecutive iterations (after which the training was aborted). Note that the below chart only illustrates episode 400 to 500 even if they are denoted 0 - 100.

|           |            |
| :-------------: |:-------------:|
| ![Results graph](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/2.%20Project%202%20-%20Continuous%20Control/32DF63ED-C0C0-4B4A-B81C-A38CE98387B0.png "Results graph")  | ![Results table](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/2.%20Project%202%20-%20Continuous%20Control/24EBF224-C5AA-40FD-B2E4-7D782166CE73.png "Results table") |

### 5. Next steps

- Improving the results by tweaking the many static variables set in this model could be a next step to take to simply try out different settings. 
- Further, Prioritized Experience Replay can be a good idea since we use an experience replay buffert.
- Last, I decided to use a DDPG model, however, there are other possible models to use such as PPO or TRPO that could be a better fit for the challenge.
