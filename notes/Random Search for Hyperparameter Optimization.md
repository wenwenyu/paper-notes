## Random Search for Hyperparameter Optimization

##### **Y. Bengio, J. Bergstra (2012)**

Summary: The paper starts by stating grid search and manual search are two commonly used strategies for hyper-parameter optimization.  The paper claims that in theory and in practice random trials are more efficient for hyper-parameter optimization than alternative methods.  

### Datasets 
The paper tested the effectiveness of dropout using the MNIST dataset.  The dataset contains 60,000 training images, and 10,000 test images.  Performance on the test set can be greatly improved by enhancing the training data with transformed images, by wiring knowledge about spatial transformations into a CNN, or by using generative pre-training to extract useful features from the training images  without using the labels.  Experiments were also performed on (1) the TIMIT dataset, a commonly used benchmark for recognition of clean speech with a small vocabulary, (2) the CIFAR-10 dataset a benchmark task used for object recognition, (3) the ImageNet dataset, a well known challenging set consisting of 1000 classes with about 1000 examples per class, and (4) the Reuters dataset, a set containing documents that have been labeled with a hierarchy of classes.  

### Notes 
- A gaussian process analysis of the function from HP’s to validation set performance showed that for most datasets only a few of the HP’s matter, but that different HP’s are important on different datasets.  
- Usually a learning algorithm produces *f* through the optimization of training criterion with respect to a set of *parameters* \theta 
- The learning algorithm itself often takes values called *HP’s*.  The process of finding a good value for HP’s is called *HP optimization*.  
- The most widely used strategy is a combination of grid search and manual search.  The main drawback of manual search is the difficulty in reproducing results.  The main problem in grid search alone is that in practice it performs poorly.  

Continue after DR notes...
