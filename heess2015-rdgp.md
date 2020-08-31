# Memory based Control with Recurrent Neural Networks
## 2015, https://arxiv.org/pdf/1512.04455.pdf

Deterministic Policy Gradient Method with recurrent neural networks for solving the partial observability problem in an POMDP(Partially-Observable Markov Decision Process). DPG optimizes or shifts the probability mass to a deterministic policy, while continuing to explore through its Stochastic Behavior Policy.
SVG- Stochastic Value Gradient:- On-policy Algorithm - optimizies a stochastic policy.


#### Key Points in the Paper:
1.
2. There are cases when deterministic policies fail under partial observability, and which requires optimizing a stochastic policy. The SVG and the RSVG are really good at these as they try to optimize a stochastic policy or the policy they use for exploring the state space.
3. So for the RSVG, a stochastic plicy is represented in terms of a fixed independent noise and a parametric deterministic function that samples from the noise source. For instance we are to develop a policy which is sampled from a gaussian distrbution, then it can parameterized as a mean and standard deviation such as the mean is given by the parametric deterministic function and the standard devaition is multiplied by a standard gaussian noise with zero mean and standard deviation = 1.
4. They store the experienced trajectories and calculates the expected value of sum of discounted rewards with trajectories sampled from that database.
Target Networks:

Soft updates of the weights/parameters on the target networks is done.

#### Algorithm and Network Architecture:

Nothing much regarding the network architecture was dicussed in the paper(like the number of layers, number of LSTM Blocks etc..), but the algorithm dicusses about the use of target networks

####  Results and Discussion:
They implement the RDPG-LSTM on various types of partially-observable control problems and obtain good results.
1. 
2. They varied the pole length for the cart-pole problem integrating the sensor-information problem with the system identification, to see if the network tries to infer the underlying dynamics of the cartpole to learn a policy.
3. They give high-dimensional visual input(image frames of a planar 5-R robot with target location) and the robot is made to reach a target location whose information is not displayed after the first five subsequent frames, and the robot is not made to move during that time to avoid encoding the target location and encouraging the network to learn after that.
