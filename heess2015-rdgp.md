# Memory based Control with Recurrent Neural Networks
## Year: 2015, Link to the Paper: https://arxiv.org/pdf/1512.04455.pdf

Deterministic Policy Gradient Method with recurrent neural networks for solving the partial observability problem in an POMDP(Partially-Observable Markov Decision Process). DPG optimizes or shifts the probability mass to a deterministic policy, while continuing to explore through its Stochastic Behavior Policy.
DPG - Deterministic Policy Gradient:- Off-Poicy Algorithm
SVG- Stochastic Value Gradient:- On-policy Algorithm - optimizies a stochastic policy.

s- State,
a - action,
Q - Action Value,
mu - Policy.
#### Key Points in the Paper:
1. The objective function is over the discounted state visitation distribution.The Q(w)(critic) is learned through a function approxmiator such as a NN(in this case NN with SLTM Blocks).
State Visitation Distrbution : Discounted sum of probabilities of visting a given state under a given policy.
(Link for a good explanation on state visitation Distribution:
https://www.alexirpan.com/rl-derivations/#:~:text=The%20state%20visitation%20frequency%20is,of%20visiting%20a%20given%20state.&text=Note%20that%20up%20to%20a,a%20probability%20distribution%20over%20states.&text=More%20precisely%2C%20multiplying%20%CF%81%CF%80,%CE%B3)%20gives%20a%20probability%20distribution.)
2. Two copies of the Value function network and the Policy network are made. Out of which we have critic network for Q and actor for mu and target networks for both.
##### The target network is used to learn the target values, which are then used as labels for the Critic network(i.e to update the weights in the critic network). weights/parameters are updated such that the target values don't change drastically. 
##### Refer this paper for good explanation: CONTINUOUS CONTROL WITH DEEP REINFORCEMENTLEARNING; Link: https://arxiv.org/pdf/1509.02971.pdf. 
##### The main reason to use the target networks for the target values is to avoid divergence arising from the updates of the Q i,e critic network, when learning the Q-value estimates.
3. Under partial observability, the optimal policy and the value function are  functions of the entire trajectories upto that time step. So the Q(s,a), mu(s) changes to Q(h,a) and mu(h). So, the expectation is also over the entire trajectories which are drawn from a trajectory distrbution developed under current policy.
4. There are cases when deterministic policies fail under partial observability, and which requires optimizing a stochastic policy. The SVG and the RSVG are really good at these as they try to optimize a stochastic policy or the policy they use for exploring the state space.
5. So for the RSVG, a stochastic plicy is represented in terms of a fixed independent noise and a parametric deterministic function that samples from the noise source. For instance we are to develop a policy which is sampled from a gaussian distrbution, then it can parameterized as a mean and standard deviation such as the mean is given by the parametric deterministic function and the standard devaition is multiplied by a standard gaussian noise with zero mean and standard deviation = 1.
6. They store the experienced trajectories and calculates the expected value of sum of discounted rewards with trajectories sampled from that database.
7. Soft updates of the weights/parameters on the target networks is done. 

#### Algorithm and Network Architecture:

Nothing much regarding the network architecture was dicussed in the paper(like the number of layers, number of LSTM Blocks etc..), but the algorithm dicusses about the use of target networks

####  Results and Discussion:
They implement the RDPG-LSTM on various types of partially-observable control problems and obtain good results.
1. 
2. They varied the pole length for the cart-pole problem integrating the sensor-information problem with the system identification, to see if the network tries to infer the underlying dynamics of the cartpole to learn a policy.
3. They give high-dimensional visual input(image frames of a planar 5-R robot with target location) and the robot is made to reach a target location whose information is not displayed after the first five subsequent frames, and the robot is not made to move during that time to avoid encoding the target location and encouraging the network to learn after that.
