## Random Search for Hyperparameter Optimization

##### **Y. Bengio, J. Bergstra (2012)**

Summary: The paper starts by stating grid search and manual search are two commonly used strategies for hyper-parameter optimization.  The paper claims that in theory and in practice random trials are more efficient for hyper-parameter optimization than alternative methods.  

### Notes 
- A gaussian process analysis of the function from HP’s to validation set performance showed that for most datasets only a few of the HP’s matter, but that different HP’s are important on different datasets.  
- Usually a learning algorithm produces *f* through the optimization of training criterion with respect to a set of *parameters* \theta 
- The learning algorithm itself often takes values called *HP’s*.  The process of finding a good value for HP’s is called *HP optimization*.  
- The most widely used strategy is a combination of grid search and manual search.  The main drawback of manual search is the difficulty in reproducing results.  The main problem in grid search alone is that in practice it performs poorly.  
- The authors describe the HP configuration space of their neural network in terms of the distribution that was used to randomly sample from that configuration space

...HP in their configuration was the type of *data pre-processing* w/ equal probability one of (a) none, (b) normalize (center each feature dimension and divide by its standard deviation), or (c) PCA.  
… 2. Part of PCA preprocessing is choosing how many components to keep.  We choose a fraction of variance to keep with a uniform distribution between .5 and 1.0.  
… 3. There have been several suggestions for how the random weights should be initialized.  The possible distributions were (a) uniform(-1, 1), and (b) unit normal 
… 4. The number of hidden units was drawn geometrically from 18 to 1024
… 5. The nonlinearity was either a sigmoidal or tanh with equal probability.  
… 6. The cost function was the mean error over mini batches of either 20 or 100 examples at a time.  
… 7. The optimization algorithm was stochastic gradient descent with learning rate drawn from a geometric distribution from .001 to 10.  
… 8. The authors also offered the possibility of an annealed learning rate drawn from a geometric distribution from 300 to 3000
… 9. With 50% chance probability that an L2 regularization penalty was applied, whose strength which was drawn exponentially from 3.1 x 10 ^ -7 to 3.1 x 10 ^ -5 
- Typically the extent of a grid search is determined by computational budget.  The tradeoff between exploration and exploitation is central to the design of an effective random search
- The importance of different HPs varies depending on the dataset, but overall learning rate seemed like an important parameter (see Figure. 7)

Continue after …

### Datasets 
- **MNIST Basic** : A subset of the well known MNIST handwritten digit data set.  The images are presented as white foreground digits against a black background.  The authors applied a number of transformations on the dataset, and used those datasets as well.  The transformations were borken into five additional sets.  MNIST Rotated, MNIST Background Random, MNIST Background Images, and MNIST Rotated Background Images.  
- **Rectangles**: Is a simple synthetic data set of outlines of rectangles.  The outlines are white and the backgrounds are black.  The height and width of the rectangles were sampled uniformly, but when their difference was smaller than 3 pixels the samples were rejected.  The rectangles images dataset was a transformation of the original rectangles dataset
- **Convex**: 28 x 28 image consists entirely of 1-valued and 0-valued pixels 
