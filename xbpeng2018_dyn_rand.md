# Sim-to-Real Transfer of Robotics Control with Dynamics Randomizations 
## 2018, https://xbpeng.github.io/projects/SimToReal/2018_SimToReal.pdf

Dynamics Randomization: Randomize the dynamic properties or the physics parameters of the simulators and train the networks to generate policies. The policies developed are well able to adapt to different dynamics than the dynamics that they were trained on. The intuition here is that by doing this, the policies can be generalized to dynamics of the real world. They obtain good results on the real hardware by just training the policies on simulation. The policies developed were for pushing objects on a table from random initial configurations to a target location.

s-state
a-action
g-goal

#### Key Points in the Paper:
1. Objective to achieve universal policy, the goal is provided as an additional input to the policy i.e the policy maps s,g to a pi(a/s,g). Here the goals are the random traget locations for the object/puck to be manipulated on the table. The goal changes after every episode
2. Has only binary rewards i.e *0* if the goal is satisfied or -1.
3. Employs Hindight Experience Replay for exploration(it is an off-policy algorithm) and deals with the sparse rewards(no specified reward function is required to achieve the task). The idea here is that in an episode, if an agent is not able to reach the original goal and if there is a mapping from let'say, the final state to goal(i.e a new goal/final state which is satified by the trajectory), then the rewards computed w.r.t the new goal will not be -1 for every step, and giving some insights on how to develop the policies. So by replaying past experiences with HER, the agent can be trained with more succesful data, than that will be available with just the original trajectories.
4. Uses the recurrent model of the Deterministic Policy-Gradient method to optimize the policy to maximize over all the random dynamic properties of the simulated environments. 
a. HER can be used to deal with sparse rewards.
b. DPG is an Offline policy gradient method that can benefit with the HER.
c. Also, easy for the System Identification to infer the underlying dynamics of the system.
5. Embeds the system identification directly into the value function learning network as the internal memory. The Dynamics parameter is only used in value function and not the policy network.


#### Network Architecture:

1. Learning the Policy (Output is a 7-D Joint angles of the manipulator).
2. Learning the Value function(Output is n continuous Real Space of 1-D ).

Optimizer: ADAM with step size: 5x10^-4.

#### Results:
1. Different network architectures were compared and analysed.
2. Recurrent network achieves the best performance, also verified its robustness by changing the contact dynamics while evaluating on the physical system.
3. Performance order: LSTM > FF + Hist > FF > FF no randomization.
3rd result clealrly indicating that the "Dynamic Randomization indeed was useful in learning the policy".








