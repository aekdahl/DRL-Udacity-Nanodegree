Continouos Control
# Project 1 - Navigation

![Unity Environment](https://github.com/aekdahl/DRL-Udacity-Nanodegree/blob/master/1.%20Project%201%20-%20Navigation/img1.png "Unity Environment")

## Project Overview

This is the first project in the Udacity Nanodegree for Deep reinforcement Learning. The notebook showcase how to train a Unity ML-Agent to navigate in a game-like environment and picking yellow bananas while avoiding blue ones. Essentialy, the agent learns to navigate and solves a classification problem (it needs to distinguish between blue and yellow bananas). The agent does this by selecting one out of 4 possible actions in each state (time point) and gets rewarded +1 when it selets a yellow banana, and -1 for picking a blue one. The goal for the agent is then to simply figure out how to end up with as high reward as possible.

## Get started

Ensure python 3.6 is installed on your system, then install and import the required python packages. The essential packages are UnityAgents, PyTorch and NumPy (already taken care of in the notebook).

```python
!pip install unityagents
!pip install torch
from unityagents import UnityEnvironment
import numpy as np
import random
from collections import namedtuple, deque

import torch
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim

import matplotlib.pyplot as plt
%matplotlib inline
```

## Instructions
Run the Project 1 - Navigation notebook to get step by step instructions on the code and how to train the agent.
