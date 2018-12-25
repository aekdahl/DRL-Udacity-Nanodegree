# Project 2 - Continouos Control

![Unity Environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/images/reacher.png "Unity Environment")

## Project Overview

This is the second project in the Udacity Nanodegree for Deep reinforcement Learning. The notebook showcase how to train 20 Unity ML-Agents to control double-jointed arms by moving them to target locations. Essentially, the agents build a shared pool of experience used to train the algorithm on. By doing multiple agents simultaneously the experience pool is built faster and with greater variety of experiences allowing the trained agent to be better than the equivalent using only one agent. Each agent control a double-jointed arm using continouos values as action inputs. Each action is a vector with four numbers, corresponding to torque applicable to two joints. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible. The problem is considered solved when the agent (in this case the average of 20 agents) achieves +30 points across 100 consequtive runs in the environment.

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

import matplotlib.pyplot as plt
%matplotlib inline
```

## Instructions
Run the Project 2 - Continouos Control notebook to get step by step instructions on the code and how to train the agents.
