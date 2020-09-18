# TuneNet: One-Shot Residual Tuning for System Identification and Sim-to-Real Robot Task Transfer

## Year: 2020, Link to the Paper: https://arxiv.org/pdf/1907.11200.pdf

#### Notation:
1. Observation - o
2. Action - a
3. State - s
#### Key Points:
1. Performs to learn the difference transformation directly on the physics parameters of the models of the system, rather than on the trajectories(s,a) like the domain adaptation paper. 
2. Establishes a Supervised learning problem to model or estimate the difference/residual of the physics parameters and does not estimate the parameters directly.
3. Iteratively updates the parameters of the proposed model by adding the estimated residual to the previous update of the model. 
4. Uses only one observation from the real world data for the Sim-to-real training and resamples it according to the length and freqency of the observations from simulations.
5. Main Assumption is that there would be atleast a set of parameters (from the whole set of paramters of a propsed model) that could be made sure to closely match the physics parameters of the real world or the target model. and uses this proposed model(i.e the model trained on simulated dataset) as the prior in the iterative optimization/tuning. 
6. And Uses only observations(o) unlike the other recent works which use trajectories i,e(o,a)

#### Network Architecture and Algorithm:
1. Firstly, performs a supervised learning on datasets obtained completely from the simulations.
2. Uses Observations from two environments/Simulations with different physics parameters choosing model from one simulation as the target and the other one as the proposed model and tries to estimate the difference in the physics parameters between them. Produces a NN model of the same.(i.e the model of the residual).
3. Then uses observation from the real world to iteratively update the propsed model by estimating the residual for each iteration with the addition of the proposed model up to the current iteration. 

#### Results on Sim-to-real Learning for System Identification:
1. Can fail if asked to estimate the paramteres accurately.
2. No policy is learnt while on Simuulation or no controller is learnt. But this can be used in conjunction with learning a policy using some Deep RL or RL. 
3. But the system identification for a Sim-to-real problem is achieved with less iterations.
4. Works good in the real world even with an inaccurate estimation of the coefficient of restitution for a ball bouncing task. 
