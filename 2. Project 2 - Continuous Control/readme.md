# Project 2 - Continouos Control

![Unity Environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/images/reacher.png "Unity Environment")

## Project Overview

This is the second project in the Udacity Nanodegree for Deep reinforcement Learning. The notebook showcase how to train 20 Unity ML-Agents to control double-jointed arms by moving them to target locations. Essentially, the agents build a shared pool of experience used to train the algorithm on. By doing multiple agents simultaneously the experience pool is built faster and with greater variety of experiences allowing the trained agent to be better than the equivalent using only one agent. Each agent control a double-jointed arm using continouos values as action inputs. Each action is a vector with four numbers, corresponding to torque applicable to two joints. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible. The problem is considered solved when the agent (in this case the average of 20 agents) achieves +30 points across 100 consequtive runs in the environment.

## Get started
Ensure python 3.6 is installed on your system, then please follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

Next, you need to select and download the environment that matches your operating system:

Version 2: Twenty (20) Agents
Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

Then, place the file in the p2_continuous-control/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.

## Instructions
Run the Project 2 - Continouos Control notebook to get step by step instructions on the code and how to train the agents.
