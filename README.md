# Continuous Control

[Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) Continuous Control project.

Train an agent with DRL to control a double-jointed arm to move to a target location.

## Project Setup

### Introduction

In this project, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The task is episodic, and in order to solve the environment, the agent must get an average score of +30 over 100 consecutive episodes.

### Getting Started

Setup the environment as detailed [here](https://github.com/udacity/deep-reinforcement-learning/blob/master/p2_continuous-control/README.md#getting-started).

### Requirements

 * [Unity ML-Agents](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md)
 * [NumPy](http://www.numpy.org/)

## Training

Follow the instructions in [Continuous_Control.ipynb](Continuous_Control.ipynb) file to train the agent.

## Report

The associated report is detailed on the [Report.md](Report.md) file.

## Evaluation

Sample evaluation of the agent can be checked on [this video](extra/cc01.mp4) file.