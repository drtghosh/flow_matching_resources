# Flow Matching

## Possible things to try

### Different Loss Functions/Optimizations used for straight/linear trajectories
1. Smart Flow Matching (https://arxiv.org/abs/2402.03232) paper:
    a. Claims to be converging faster with modified loss (try the new loss) 
        Doubts: Need much more sample from unknown distribution! DO WE HAVE THAT?? Maybe coz point cloud data are available now-a-days
    b. Rather than just straight flow (linear combo) try regularized map such as linear map with Gaussian noise
2. Optimal Flow Matching (https://arxiv.org/abs/2403.13117) paper:
    a. While each Reflow/Rectify flow in Flow Straight and Fast paper straightens the flow map trajectories, with each iteration it also accummulates error which leads to worse performance. But OFM claims to find the optimal straight flow in one iteration by optimizing over 'Optimal vector fields' (only convex functions which generates linear trajectories as flows) with a modified loss function.
    b. In comparison with Rectified Flow and Minibatch OT Optimal Flow Matching returns optimal unbiased solution, requires only one iteration of minimization.
        Doubts: Whether convex function restriction will work in 3D data well enough!

### Different SNR Samplers (Timestep sampling modification):
1. Scaling Rectified Flow Transformers for High-Resolution Image Synthesis (https://arxiv.org/abs/2403.03206) paper:
    a. Try to improve existing noise sampling techniques for training rectified flow models by biasing them towards perceptually relevant scales.
    b. The Rectified Flow loss trains the velocity uniformly on all timesteps in [0, 1]. Intuitively, however, the resulting velocity prediction target is more difficult for t in the middle of [0, 1], since for t = 0, the optimal prediction is the mean of p1, and for t = 1 the optimal prediction is the mean of p0. In general, changing the distribution over t from the commonly used uniform distribution to a distribution with more weight to intermediate timesteps by sampling them more frequently.

### Straightening the trajectory
1. Minimizing Trajectory Curvature of ODE-based Generative Models (https://arxiv.org/abs/2301.12003) paper:
    a. Joint training of noise and data coupling to minimize intersection in trajectory
        Doubt: how complex the architecture would be (have to check more)
2. Multisample Flow Matching: Straightening Flows with Minibatch Couplings (https://arxiv.org/abs/2304.14772) paper:
    a. Similar idea where shown that for certain joint distributions (constructed via a doubly-stochastic matrix), the straightness of the flow is close to zero.

### Likelihood Estimation
1. Improved Techniques for Maximum Likelihood Estimation for Diffusion ODEs (https://arxiv.org/abs/2305.03935)
2. Flow Matching for Scalable Simulation-Based Inference (https://arxiv.org/abs/2305.17161)

### Distillation Step
1. Use other distance measures to compare point clouds instead of Chamfer (EMD is computationally expensive, so maybe use Sliced Wasserstein distance??)
