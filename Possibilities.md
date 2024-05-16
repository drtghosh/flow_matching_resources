# Flow Matching

## Possible things to try

### Different Loss Functions/Optimizations used for straight/linear trajectories

1. Smart Flow Matching paper:
    a. Claims to be converging faster with modified loss (try the new loss) 
        Doubts: Need much more sample from unknown distribution! DO WE HAVE THAT?? Maybe coz point cloud data are available now-a-days
    b. Rather than just straight flow (linear combo) try regularized map such as linear map with Gaussian noise
2. Optimal Flow Matching paper:
    a. While each Reflow/Rectify flow in Flow Straight and Fast paper straightens the flow map trajectories, with each iteration it also accummulates error which leads to worse performance. But OFM claims to find the optimal straight flow in one iteration by optimizing over 'Optimal vector fields' (only convex functions which generates linear trajectories as flows) with a modified loss function.
    b. In comparison with Rectified Flow and Minibatch OT Optimal Flow Matching returns optimal unbiased solution, requires only one iteration of minimization.
        Doubts: Whether convex function restriction will work in 3D data well enough!

