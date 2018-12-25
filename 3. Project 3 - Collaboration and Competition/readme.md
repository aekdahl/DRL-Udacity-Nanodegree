# Project 3 - Collaboration and Competition

![Unity Environment](https://github.com/Unity-Technologies/ml-agents/raw/master/docs/images/tennis.png "Unity Environment")

## Project Overview

This is the third and final project in the Udacity Nanodegree for Deep reinforcement Learning. The notebook showcase how to train two competing Unity ML-Agents to play a "slightly" modified version of tennis. Essentialy, each agent learns to keep the ball from touching the ground and to hit it back to the opponents side. The agents does this by providing an action vector in each state (timestep) and gets rewarded +0.1 when it manage to hit the ball over the net, and -0.01 failing to do so, and letting the ball hit the ground.

## Get started

Ensure python 3.6 is installed on your system, then install and import the required python packages. The essential packages are UnityAgents, PyTorch and NumPy (already taken care of in the notebook).

```python
!pip install unityagents
!pip install torch
from unityagents import UnityEnvironment
import numpy as np

import torch
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim

import matplotlib.pyplot as plt
%matplotlib inline
```

## Instructions
Run the Project 3 - Collaboration and Competition notebook to get step by step instructions on the code and how to train the agents.
