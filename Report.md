# Project Continuous Control

My solution for the [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) Continuous Control project, following the [Rubric](https://review.udacity.com/#!/rubrics/1890/view).

[//]: # (Image References)

[image1]: ./extra/train_episodes.png

---
## Description

The objective is to train an agent to navigate (and collect bananas) in a large, square world. It was used a `Deep Q Learning` algorithm where a 2 hidden layer deep neural network model was trained to estimate the expected reward of each action at any state.

Internally two separate networks are used for learning. The `Local` network to learn the parameters at every step and the `Target` network to estimate the target value. During every step, the experience is stored in a `Replay Buffer` memory which will be used to train the agent on every step.

### Training

All training was done on the [Continuous_Control.ipynb](Continuous_Control.ipynb) notebook.

A plot of rewards per episode is illustrated here:

![Training result][image1]

### Evaluation

The evaluation of the agent for a couple of episodes can be checked on [this video](extra/dqt_test01.mp4); related to:

```python
code
```

### Discussion and Further Work

### Troubleshooting

### Resources

* [Setting up a Reinforcement Learning Task with a Real-World Robot](https://arxiv.org/pdf/1803.07067.pdf)
* [How Robots Can Acquire New Skills from Their Shared Experience](https://ai.googleblog.com/2016/10/how-robots-can-acquire-new-skills-from.html)
* [PPO](https://arxiv.org/pdf/1707.06347.pdf)
* [A3C](https://arxiv.org/pdf/1602.01783.pdf)
* [D4PG](https://openreview.net/pdf?id=SyZipzbCb)
