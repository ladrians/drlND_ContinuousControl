# Project Continuous Control

My solution for the [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) Continuous Control project, following the [Rubric](https://review.udacity.com/#!/rubrics/1890/view) for the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/release_4_branch/docs/Learning-Environment-Examples.md#reacher) environment.

[//]: # (Image References)

[image1]: ./extra/cc01_train.png
[image2]: ./extra/cc01.gif

---
## Description

The objective is to train a double-jointed arm to move to target locations.

A reward of `+0.1` is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of `33` variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between `-1` and `1`.

## Architecture

The initial configuration uses the [ddpg-bipedal](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal) project architecture. Internally the `ddpg` (Deep Deterministic Policy Gradient) agent with `experience replay` was implemented.

I used a vanilla deep neural network consisting of 3 fully connected layers for the `actor` and `critic`. The `actor` approximates the best action in the given state while the `critic` approximates the associated `Q-value `.

### Hyperparameters

The initial configuration from the [ddpg-bipedal](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal) project uses:

```python
BUFFER_SIZE = int(1e6)  # replay buffer size
BATCH_SIZE = 128        # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR_ACTOR = 1e-4         # learning rate of the actor
LR_CRITIC = 3e-4        # learning rate of the critic
WEIGHT_DECAY = 0.0001   # L2 weight decay
```

It was detected unstability during training. The following parameter changes were tested:

 * `BATCH_SIZE`: `32`, `64`, `128`, `256` using a default of `64`.
 * `LR_ACTOR`: from `1e-3` to `1e-4`.
 * `LR_CRITIC`: `1e-3`, `3e-4` to `1e-4`.
 * `SIGMA`: from  `0.2`, `0.85`, `0.05` to `0.1`.

Modifying the batch size in combination with the exploring noise from the `Ornstein-Uhlenbeck` process got better results.

## Training

### One Agent

All training was done on the [Continuous_Control.ipynb](Continuous_Control.ipynb) notebook, taking as reference the [DDPG algorithm](https://arxiv.org/abs/1509.02971) from the [ddpg-bipedal](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal) code section.

The result (local execution) is as follows using 900 episodes:

```python
Episode 100	Average Score: 2.92	Score: 4.39
Episode 200	Average Score: 10.54	Score: 18.28
Episode 300	Average Score: 18.46	Score: 25.58
Episode 400	Average Score: 23.68	Score: 23.67
Episode 500	Average Score: 23.49	Score: 25.86
Episode 600	Average Score: 22.91	Score: 25.41
Episode 700	Average Score: 26.08	Score: 26.39
Episode 800	Average Score: 25.57	Score: 25.32
Episode 900	Average Score: 26.02	Score: 27.68
```

A plot of rewards per episode is illustrated here:

![Training result][image1]

### Evaluation

The evaluation of the agent for a couple of episodes can be checked on [this video](extra/cc01.mp4):

![Training evaluation][image2]

## Discussion and Further Work

A basic agent was implemented to solve the task using the `DDPG` algorithm. More experimentation is needed on the hyperparameters to get better results, or to change the architecture to a multiple (non-interacting, parallel) copies of the same agent so as to distribute the task of gathering experiences. Besides, could be useful to explore other algorithms such as `PPO`, `A2C`/`A3C`.

## Resources

* [Setting up a Reinforcement Learning Task with a Real-World Robot](https://arxiv.org/pdf/1803.07067.pdf)
* [How Robots Can Acquire New Skills from Their Shared Experience](https://ai.googleblog.com/2016/10/how-robots-can-acquire-new-skills-from.html)
* [Proximal Policy Optimization Algorithms](https://arxiv.org/abs/1707.06347)
* [Asynchronous Methods for Deep Reinforcement Learning](https://arxiv.org/abs/1602.01783)
* [Continuous control with deep reinforcement learning](https://arxiv.org/abs/1509.02971)
* [D4PG](https://openreview.net/pdf?id=SyZipzbCb)
* [Benchmarking Deep Reinforcement Learning for Continuous Control](https://arxiv.org/abs/1604.06778)
