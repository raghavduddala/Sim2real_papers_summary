# Sim-to-Real Transfer of Robotics Control with Dynamics Randomizations 
## 2018, https://xbpeng.github.io/projects/SimToReal/2018_SimToReal.pdf

Dynamics Randomization: Randomize the dynamic properties or the physics parameters of the simulators and train the networks to generate policies. The policies developed are well able to adapt to different dynamics than the dynamics that they were trained on. The intuition here is that by doing this, the policies can be generalized to dynamics of the real world. They obtain good results on the real hardware by just training the policies on simulation. The policies developed were for pushing objects on a table from random initial configurations to a target location.

The objective function for the maximization is modified as expected value over the distribution of the dynamic properties. 
$E_\mu(s) = $

Has randomized dynamic properties: 

Embeds the system identification directly into the value function and the policy as the internal memory.

Has two neteowrks for: 
1. Policy (Output is a 7-dimensional angles, which are provided as the ).
2. Value function( ).




