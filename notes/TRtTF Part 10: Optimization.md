## The Road to TensorFlow - Part 10: More on Optimization

##### **Stephen Smith**

Summary: Blog post by Stephen Smith on optimization techniques in TensorFlow.  

### Definitions 
- **Learning Rate**: How far we move in the direction of the sign of the gradient

### Optimization Techniques
- Gradient descent calculates the gradients of the loss function, and moves the weights in the direction that lowers the loss function
- Below we examine different ways of varying the general gradient descent algorithm to attack different problems
- Techniques such as simulated annealing, conjugate gradient, and colony optimization are also used but these tend to not work well with multi-layer NN’s or don’t parallelize well to run on GPU’s or distributed networks
- **MomentumOptimizer**
  - If GD is navigating down a valley with steep sides, it tends to madly oscillate from one valley wall to the other without making much progress down the valley 
  - MO tries to remedy this by tracking prior gradients and whether or not the direction is changing
    - If they are changing, then they get dampened
    - If they are staying in the same direction, then they get rewarded
- **AdagradOptimizer**
  - Optimized to find needles in haystacks, and for dealing with large sparse matrices
  - Keeps track of previous changes and amplifies the changes for weights that change infrequently and suppresses the weights for the ones that change frequently
- **AdadeltaOptimizer**
  - Extension of AdaGrad that remembers a fixed size window of previous changes.  This tends to make the algorithm less aggressive than pure Adagrad 
- **AdamOptimizer**
  - Keeps separate learning creates for each weight as well as an exponentially decaying average of previous gradients.  Combines elements of MO and AdaGrad and is fairly memory efficient
  - Known to work well for both sparse matrices and noisy data
- **RMSPropOptimizer**
  - Similar to Adam, but uses different moving averages but has the same goals
- Best arg depends on the job.  These algs have different tunable parameters, and finding the optimal parameters for each model can take a lot of computational power
- Often massaging your data or altering the random starting point can be better idea than trying a bunch of different algorithms
