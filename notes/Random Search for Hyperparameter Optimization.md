## Random Search for Hyperparameter Optimization

##### **Y. Bengio, J. Bergstra (2012)**

Summary: The paper starts by stating grid search and manual search are two commonly used strategies for hyper-parameter optimization.  The paper claims that in theory and in practice random trials are more efficient for hyper-parameter optimization than alternative methods.  

### Notes 
- A gaussian process analysis of the function from HP’s to validation set performance showed that for most datasets only a few of the HP’s matter, but that different HP’s are important on different datasets.  
- Usually a learning algorithm produces *f* through the optimization of training criterion with respect to a set of *parameters* \theta 
- The learning algorithm itself often takes values called *HP’s*.  The process of finding a good value for HP’s is called *HP optimization*.  
- The most widely used strategy is a combination of grid search and manual search.  The main drawback of manual search is the difficulty in reproducing results.  The main problem in grid search alone is that in practice it performs poorly.  

Continue after DR notes...
