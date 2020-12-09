# A User’s Guide to Calibrating Robotics Simulators

## Year: 2020, Link to the paper: https://arxiv.org/pdf/2011.08985.pdf




#### Important Result:
* They found that particle based simulated and randomized environments did a lot better than other MLSI algorithms. So, talks about Active Dynamics Randomization
* Also, algorithms with both the policy learning and the parameter estimation done together work better than other algos which only focus on the Parameter estimation alone( i.e direct MLSI with trajectories from real world and simulated env).

So, I guess the current approach with the online system identification with policy learning using the RDPG should work.
