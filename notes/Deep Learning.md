## Deep Learning 

##### **I. Goodfellow, Y. Bengio, A. Courville**

Summary: Free book on Deep Learning

### Definitions 
- **Precision**: The fraction of detections reported by model that were correct
- **Recall**: The fraction of true events that were detected (TPR)
- **F-Score**: One way to summarize the performance of the classifier with a single number as a function of precision and recall 
- **Coverage**: The fraction of examples for which the machine learning system can produce a response

### Chapter 11: Practical Methodology
- Successfully applying deep learning techniques requires more than knowledge of how the algorithms work
- During day to day development of machine learning systems, ML Engineers need to decide whether to gather more data, increase or decrease model capacity, add or remove regularizing features, improve the optimization of a model, improve approximate inference in am model, or debug the implementation of the model 
- Follow this general system 
  1. Determine goals - error metric to use? target value for this error metric? should be driven by the problem that application is intended to solve 
  2.  Establish a working end-to-end pipeline ASAP, including the approximation of the performance metrics
  3.  Diagnose which components are performing worse than expected and whether it is due to overfitting, underfitting, or a defect in the data or software
  4.  Repeatedly make incremental changes such as gathering new data, adjusting hyper parameters, or changing algorithms, based on specific findings 
- Default Baseline Models 
- Depending on complexity, you want not want to start with deep learning.  Try choosing a few linear weights, or simple logistic regression  
- Choose the general category of your model based on the structure of your data
  1.  Supervised learning w/ fixed-size vectors as inputs: FF NN w/ FC layers 
  2.  Input has known topological structure: Use a CNN 
  3.  In these cases use some kind of piecewise linear unit 
  4.  I/O is a Sequence: use a gated recurrent net (LSTM or GRU)
- Optimization Algorithms
  1.  SGD w/ momentum with a decaying learning rate (popular decay schemes: linear decay, exponential decay, decrease learning rate by a factor of 2-10 each time validation error plateaus)
  2.  Adam 
  3.  Batch Normalization (works especially well w/ CNN’s and networks w/ sigmoidal nonlins)
- With the exception of using tens of millions of training examples, some type of regularization should be used
 - In domains such as computer vision, current unsupervised techniques do not bring a benefit, except in the semi-supervised setting
- After the first end-to-end system is established, it is time to measure the performance of the algorithm and determine how to improve it.  Usually better to gather more data than to improve the learning algorithm
- training performance acceptable => measure test performance 
- test performance acceptable => done 
- test performance unacceptable => gather more data (tends to be effective solution, but can be costly)
- Alternative to gathering more data is to reduce the size of the model or improve regularization, by adjusting hyper parameters such as weight decay coefficients
- |train - test| gap too large after hyperparemter adjustment => more data
- Some HP’s affect the time and memory cost of running the algorithm.  Some of these HP’s affect the quality of the model
- Two approaches: (1) Choose HP’s manually (2) Choose them automatically 
- Automatic selection is usually more costly 
- LR is perhaps the most important learning parameter.  Effective capacity of the model is highest when it is correct - not when it is especially high or especially small
- When LR is too large, GD can inadvertently increase instead of decreasing the training error
- When LR is too small, training may become permanently stuck with a high training error 
- Tuning params other than LR requires analysis of train/test error to diagnose whether your model is overfitting or underfitting
- In many problems, optimization does not seem to be a significant barrier, provided that the model is chosen appropriately
