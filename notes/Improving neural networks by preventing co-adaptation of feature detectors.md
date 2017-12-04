## Improving neural networks by preventing co-adaptation of feature detectors

##### **G.E. Hinton, N. Srivastava, A. Krizhevsky, I. Sutskever, R. R. Salakhutdinov (2012)**

Summary: The paper starts by addressing the problem that arises when a a large neural network is trained on a small data set which leads to recognition of complex co-adaptions that are specific to the training images.  When the trained network is then applied to a test dataset it gives significantly lower accuracy.  The paper suggests “dropout“ as a potential solution to this problem.  On each presentation of each training case, the hidden units in the network are omitted with some probability.  It can also be though of as model averaging, since it is very unlikely that any two training images will have the same hidden units activated.  

Datasets: The paper tested the effectiveness of dropout using the MNIST dataset.  The dataset contains 60,000 training images, and 10,000 test images.  Performance on the test set can be greatly improved by enhancing the training data with transformed images, by wiring knowledge about spatial transformations into a CNN, or by using generative pre-training to extract useful features from the training images  without using the labels.  Experiments were also performed on (1) the TIMIT dataset, a commonly used benchmark for recognition of clean speech with a small vocabulary, (2) the CIFAR-10 dataset a benchmark task used for object recognition, (3) the ImageNet dataset, a well known challenging set consisting of 1000 classes with about 1000 examples per class, and (4) the Reuters dataset, a set containing documents that have been labeled with a hierarchy of classes.  

### Notes 
- The authors used a variety of different dropout probabilities and almost all of them improve the generalization performance of the network.  For FC dropout in all hidden layers works better than dropout in only one hidden layer
- Dropout is easier to implement than Bayesian model averaging which weights each model by its posterior probability given the training data
- A popular alternative to Bayesian model averaging is “bagging“
- Dropout can be thought of an extreme form of “bagging” in which each model is trained on a single case
### Results 
**MNIST**: Without using any of the tricks mentioned in the dataset section the neural network got 160 errors on the test set.  This was reduced to about 130 errors by using 50% dropout with separate L2 constraints on the incoming weights of each hidden unit.  The number of errors was reduced even further to 110 by also dropping out a random 20% of the pixels in the input images.  

**TIMIT**: Dropout with probability .5 significantly improves classification for a variety of different network architectures.  Without dropout, the recognition rate is 22.7% and with dropout this improved to 19.7%

**CIFAR-10**: The best published error rate on the test set, without transformed data is 18.5%.  By using a a neural net with three convolutional hidden layers interleaved with three “max-pooling” layers the authors achieved an error rate of 16.6% 

**ImageNet**: In 2010 a subset of this dataset was used to start an object recognition challenge.  The winning entry achieved an error rate of 47.2%.  The best result (at the time of this paper) was 45.7%.  Using a single neural network with five CONV hidden layers along with two MP layers along with two globally connected layers and a final 1000-way SM layer the authors achieved 48.6% accuracy.  After applying dropout to the network the authors achieved a record 42.6%

**Reuters**: A feedforward NN with 2 FC layers of 2000 hidden units trained with back prop achieved 31.05% error on the test set.  After applying dropout with a probability of ,5 this percentage went down to 29.62% 
