# PPO-PyTorch

### UPDATE [9th April 2021] : 

- merged continuous and discrete algorithms
- linear decaying for the continuous action space  
  action_std to make training more stable for complex environments
- added different learning rates for actor and critic
- episodes, timesteps and rewards are logged in .csv files
- utils to plot graphs from log files
- utils to test and make gifs from preTrained networks
- jupyter notebook (PPO_colab.ipynb) combining all the files to train/test/plot graph/make gif/ on google colab

#### [Open in Google Colab](https://colab.research.google.com/github/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_colab.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_colab.ipynb)


## Introduction

This repository provides a Minimal PyTorch implementation of Proximal Policy Optimization with clipped objective for OpenAI gym environments. It is primarily intended for beginners in RL for understanding the PPO algorithm. It can still be used for complex environments 
but may require some hyperparameter-tuning or changes in the code.

A concise explaination of PPO algorithm can be found [here](https://stackoverflow.com/questions/46422845/what-is-the-way-to-understand-proximal-policy-optimization-algorithm-in-rl)

To keep the training procedure simple : 
  - I have kept a constant standard deviation for the output action distribution (multivariate normal with diagonal covariance matrix) for the continuous environments, i.e. it is a hyperparameter and NOT a trainable parameter. However, it is linearly decayed.(action_std significantly affects performance)
  - I have used simple monte-carlo estimate for calculating returns and NOT Generalized Advantage Estimate (you can check out the OpenAI spinning up implementation for that or try implementing it yourself).
  - It is a single threaded implementation, i.e. only one worker collects experience [one of the forks [Link] of this repository has been modified to have Parallel workers]



## Usage

- To train a new network : run `train.py`
- To test a preTrained network : run `test.py`
- To plot graphs using log files : run `plot_graph.py`
- To save images for gif and make gif using a preTrained network : run `make_gif.py`
- All parameters and hyperparamters to control training/testing/graphs/gifs/ are in their respective `.py` files
- `PPO_colab.ipynb` combines all the files in a convenient jupyter-notebook

#### [Open in Google Colab](https://colab.research.google.com/github/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_colab.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_colab.ipynb)



## Results


| PPO Continuous RoboschoolWalker2d-v1  | PPO Continuous RoboschoolWalker2d-v1 |
| :-------------------------:|:-------------------------: |
| ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_gifs/RoboschoolWalker2d-v1/PPO_RoboschoolWalker2d-v1_gif_0.gif) |  ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_figs/RoboschoolWalker2d-v1/PPO_RoboschoolWalker2d-v1_fig_0.png) |


| PPO Continuous BipedalWalker-v2  | PPO Continuous BipedalWalker-v2 |
| :-------------------------:|:-------------------------: |
| ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_gifs/BipedalWalker-v2/PPO_BipedalWalker-v2_gif_0.gif) |  ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_figs/BipedalWalker-v2/PPO_BipedalWalker-v2_fig_0.png) |


| PPO Discrete CartPole-v1  | PPO Discrete CartPole-v1 |
| :-------------------------:|:-------------------------: |
| ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_gifs/CartPole-v1/PPO_CartPole-v1_gif_0.gif) |  ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_figs/CartPole-v1/PPO_CartPole-v1_fig_0.png) |


| PPO Discrete LunarLander-v2  | PPO Discrete LunarLander-v2 |
| :-------------------------:|:-------------------------: |
| ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_gifs/LunarLander-v2/PPO_LunarLander-v2_gif_0.gif) |  ![](https://github.com/nikhilbarhate99/PPO-PyTorch/blob/master/PPO_figs/LunarLander-v2/PPO_LunarLander-v2_fig_0.png) |


## Dependencies
Trained and tested on:
```
Python 3.6
PyTorch 1.0
NumPy 1.15.3
gym 0.10.8
Pillow 5.3.0
```

## References

- [PPO paper](https://arxiv.org/abs/1707.06347)
- [OpenAI Spinning up](https://spinningup.openai.com/en/latest/)
