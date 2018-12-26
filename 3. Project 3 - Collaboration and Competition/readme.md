# Project 3 - Collaboration and Competition

![Unity Environment](https://github.com/Unity-Technologies/ml-agents/raw/master/docs/images/tennis.png "Unity Environment")

## Project Overview

This is the third and final project in the Udacity Nanodegree for Deep reinforcement Learning. The notebook showcase how to train two competing Unity ML-Agents to play a "slightly" modified version of tennis. Essentialy, each agent learns to keep the ball from touching the ground and to hit it back to the opponents side. The agents does this by providing an action vector in each state (timestep) and gets rewarded +0.1 when it manage to hit the ball over the net, and -0.01 failing to do so, and letting the ball hit the ground. The environment is considered solved, when the average (over 100 episodes) of the scores is at least +0.5.

## Get started
Ensure python 3.6 is installed on your system, then please follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

Next, you need to select and download the environment that matches your operating system:

Version 2: Twenty (20) Agents
- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

Then, place the file in the p3_collab-compet/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.

## Instructions
Run the Project 3 - Collaboration and Competition notebook to get step by step instructions on the code and how to train the agents.
