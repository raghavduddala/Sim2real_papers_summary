# Memory based Control with Recurrent Neural Networks
## 2015, https://arxiv.org/pdf/1512.04455.pdf

Deterministic Policy Gradient Method with recurrent neural networks for solving the partial observability problem in an POMDP(Partially-Observable Markov Decision Process). DPG optimizes or shifts the probability mass to a deterministic policy, while continuing to explore through its Stochastic Behavior Policy.
SVG- Stochastic Value Gradient:- On-policy Algorithm - optimizies a stochastic policy.


#### Key Points in the Paper:
There are cases when a deterministic policy fails to achieve the task, examples
They store the experienced trajectories and calculates the expected value of sum of discounted rewards with trajectories sampled from that database.
Target Networks:

Soft updates of the weights/parameters on the target networks is done.

#### Algorithm and Network Architecture:

Nothing much regarding the network architecture was dicussed in the paper(like the number of layers, number of LSTM Blocks etc..), but the algorithm dicusses about the use of target networks

####  Results and Discussion:
They implement the RDPG-LSTM on various types of partially-observable control problems and obtain good results.
1. 
2. They varied the pole length for the cart-pole problem integrating the sensor-information problem with the system identification, to see if the network tries to infer the underlying dynamics of the cartpole to learn a policy.
3. They give high-dimensional visual input(image frames), a planar 5-R robot is made to reach a target location whose information is not displayed after the first five subsequent frames, and the robot is not made to move during that time to avoid encoding the target location and encouraging the network to learn after that.
