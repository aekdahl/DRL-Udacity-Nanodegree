Udacity - *Deep Reinforcement Learning Nanodegree* | ***Alexander Ekdahl***


# Project 1 - Navigation Report

This notebook showcase how to train a Unity ML-Agent to navigate in a game-like environment and picking yellow bananas while avoiding blue ones. 


![Unity Environment](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img1.png "Unity Environment")

### 1. Problem statement and approach
Essentialy, the agent needs to learn how to navigate the environment and solve the classification problem (it needs to distinguish between blue and yellow bananas). The agent does this by selecting one out of 4 possible actions in each state (time point) and gets rewarded +1 when it selets a yellow banana, and -1 for picking a blue one. The goal for the agent is then to simply figure out how to end up with as high reward as possible. The problem is considered solved when the agent achieves +13 points across 100 consequtive runs in the environment.

We are training the agent on 2000 episodes with a maximum of 1000 iterations (timesteps) in each episode. The aim is to reach +13 points to solve the environment, but we will let it run cross all 2000 episodes to see if we can further improve over more iterations. Note that epsilon decrease over time to decrease the amount of exploration and increase the amount of exploitation. In other words, early on, we want the agent to explore the environment, but when it has started to learn and found the "right" path, it should focus on improving performance there instead of exploring. eps_decay below indicates the amount of decrease per episode iteration.

### 2. Environment
- Number of agents: 1
- Number of states: 37
- Number of possible actions: 4 
    - *walk forward*
    - *walk backward*
    - *turn left*
    - *turn right*
- Rewards: 
    - Yellow banana: +1 
    - Blue banana: -1

### 3. Learning Model
The model is a Deep Neural Network with 3 fully connected layers. It takes the 37 different states from the state vector as input, and outputs the four possible actions (from which the action to be taken is decided). 
- Input: state_size (37), Output: 64
- Input: 64, Output: 64
- Input: 64, Output: action_size (4)

Model Parameters:
- Replay buffer size: 100.000
- Minimum batch size: 64
- Discount factor: 0.99
- Soft update of target: 0.001
- Learning rate: 0.00005
- Update network frequency: 4

Agent Parameters:
- Episodes: 2000
- Maximum timesteps: 1000
- Start eps: 1.0
- End eps: 0.01
- Decay of eps: 0.995

### 4. Result
As the below results show, the model was able to solve the environment after 600 iterations (episodes) but was able to further improve performance until it kind of evens out around 1000 episodes or so. The maximum score achieved was 16.70 across 100 consecutive iterations.

|           |            |
| :-------------: |:-------------:|
| ![Results graph](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img2.png "Results graph")  | ![Results table](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img3.png "Results table") |

### 5. Next steps

- Improving the results by tweaking the many static variables set in this model could be a next step to take to simply try out different settings. 
- From there, it seem that some of the addons to the DQN algorithm can be used to further improve the performance. Trying out Double DQN, Prioritized Experience Replay or Dueling DQN might be a good idea.
- In this model we did not use the images produced by the video game as learning input to the model. Using the pixels of the images with CNN layers may also improve the results. Quite possibly with a trade off on computational performance and cost though.
