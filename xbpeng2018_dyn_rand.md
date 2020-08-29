# Sim-to-Real Transfer of Robotics Control with Dynamics Randomizations 
## 2018, https://xbpeng.github.io/projects/SimToReal/2018_SimToReal.pdf

Dynamics Randomization: Randomize the dynamic properties or the physics parameters of the simulators and train the networks to generate policies. The policies developed are well able to adapt to different dynamics than the dynamics that they were trained on. The intuition here is that by doing this, the policies can be generalized to dynamics of the real world. They obtain good results on the real hardware by just training the policies on simulation. The policies developed were for pushing objects on a table from random initial configurations to a target location.



#### Key Points in the Paper:

1. Uses the recurrent model of the Deterministic Policy-Gradient method to optimize the policy to maximize over all the random dynamic properties of the simulated environments.
2. Embeds the system identification directly into the value function and the internal memory. The Dynamics parameter is only used in value function and not the policy.
3. Employs Hindight Experience Replay for exploration(it is an off-policy algorithm) and deals with the sparse rewards(no specified reward function is required to achieve the task).

#### Network Architecture:

1. Learning the Policy (Output is a 7-D Joint angles of the manipulator).
2. Learning the Value function(Output is n continuous Real Space of 1-D ).
Optimizer: ADAM with step size: 5

#### Results:








