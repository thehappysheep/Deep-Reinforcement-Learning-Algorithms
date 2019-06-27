# Pong with PPO

### Introduction 

In this notebook, we implement an agent learning to play Pong with
algorithm PPO ([Proximal Policy Optimization](https://openai.com/blog/openai-baselines-ppo/)).  
As with the [REINFORCE version](https://github.com/Rafael1s/Deep-Reinforcement-Learning-Udacity/tree/master/Pong-Policy-Gradient-REINFORCE), 
the model learns from pixels.

![](images/cat_pong_giphy.gif)

## Algorithm PPO 

I. Collect trajectories based on the policy \Pi(\theta'),  
initialize  \theta' = \theta.

II. Compute the gradient for the clipped surrogate function

![](images/L_CLIPPED_SURR_FUNC_2.png)

where r_t(\theta) is the ratio of new probabilities and old probabilities:

![](images/prob_ratio_B.png)

III. Gradient ascent, update \theta':

![](images/gradient_ascent.png)

IV. The internal loop of the PPO training. The loop repeats steps 2 and 3 
SGD_epoch times. This means that every trajectory is used SGD_epoch times 
before it is discarded. In our case SGD_epoch = 4. For the case REINFORCE,
SGD_epoch = 1.

V. External loop, back to step 1. Set \theta=\theta',
 go to new epsodes, and new trajectories.


## Credit   
Most of the code is based on the Udacity code for the PPO algorithm.   