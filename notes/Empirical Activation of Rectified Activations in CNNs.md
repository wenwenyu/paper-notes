## Empirical Activation of Rectified Activations in CNNs

##### **Bing Xu, Naiyan Wang, Tianqi Chen, Mu Li (2015)**

Summary: The paper starts by addressing the fact that one of the key characteristics of modern deep learning systems is the use
of non-saturated activation functions over [saturated](https://stats.stackexchange.com/questions/174295/what-does-the-term-saturating-nonlinearities-mean) ones.
The most commonly used non-saturated activation function is ReLU.  The paper examines variants of the Leaky ReLU activation 
function on the CIFAR-10/CIFAR-100 datasets along with a Kaggle dataset.  

### ReLU Variants 

#### PReLU
*PReLU* is the same as Leaky ReLU, with the exception that the parameter is learned during back propagation.  

#### RReLU 
*RReLU* is the same as Leaky ReLU, with the exception that the slopes of negative parts are randomized during training and then 
fixed during testing.  

### Results 
In both CIFAR datasets the Leaky ReLU and RReLU outperformed ReLU and PReLU on the CIFAR datasets.  More specifically the 
LReLU function with a smaller leaky coefficient performed better.
