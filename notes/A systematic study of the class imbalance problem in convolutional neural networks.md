## A systematic study of the class imbalance problem in convolutional neural networks

##### **M. Buda, A. Maki, M. A. Mazurowksi (2017)**

Summary: Paper performs an extensive comparison of methods to decrease class imbalance including oversampling, under sampling, two-phase training, and thresholding to compensate for prior class imbalance.  Based on experiments the authors made a number of conclusions:
  - The effect of class imbalance on classification performance is harmful 
  - Dominant method at addressing class imbalance was oversampling 
  - As opposed to some classical ml methods, oversampling does not cause overfitting
  - Thresholding should be applied to compensate for prior class probabilities when overall number of properly classified cases is of interest

### Dataset: Goal of the authors was to use datasets with increasing complexity
- **MNIST**: 28 x 28 x 1 images, 10 classes, 5,000 training, 1,000 testing
- **CIFAR-10**: 32 x 32 x 3 images, 10 classes, 5,000 training, 1,000 testing 
- **ImageNet**: >= 256 x >= 256 x 3 images, 1,000 classes, 1,000 training, 50 testing

### Notes
- Common problem in real life applications of deep learning based classifiers is that some classes have a significantly higher number of examples in the training set than other classes
- Has been established that CI can have significant effect on training of traditional classifiers including multi-layer perceptron.  If affects both convergence during training, and generalization of a model on the test set 
- Methods for dealing with CI are well studied for classical machine learning models.  The most straightforward is to use sampling methods (methods operate on the data itself rather than the model)
- CI can also be tackled at the classifier level.  When this is done the learning algs are modified, e.g by introducing different weights to misclassification of examples from different classes, or explicitly adjusting prior class probabilities
- CI can take many forms in the context of multi class classification:
  1.  *Step Imbalance*: the # of examples is equal within minority classes and equal within majority classes but differs between the majority and minority classes.  This form of imbalance is characterized by two params (fraction of minority classes, the ratio between the # of examples in majority classes and the # of examples in minority classes)
  2.  *Linear Imbalance*: Defined with one parameter.  The number of examples in the remaining classes as interpolated linearly such that difference between the maximum and minimum number of examples among all classes 
- Methods of addressing imbalance compared in this study: 
  1.  Random minority oversampling 
  2.  Random majority under sampling 
  3.  Two-phase training with pre-training on randomly under sampled dataset
  4.  Two-phase training with pre-training on randomly under sampled dataset
  5.  Thresholding with prior class probabilities
  6.  Oversampling with thresholding 
  7.  Undersampling with thresholding
- In the context of multi class classification with CNNs overall accuracy is the metric used to assess the model.  
- Potential Issue: When the test set is balanced and a training set is imbalanced.  Can result in a situation when a decision threshold is moved to reflect the estimated class prior probs which causes a low accuracy measure in the test set while the true discriminative power of the classifier does not change
- Authors noticed the deterioration of performance due to CI was substantial.  They also noticed that the effect of imbalance is way stronger for tasks with higher complexity
- Similar drop in performance for MNIST and CIFAR-10 corresponded to approximately 100 times stronger level of imbalance in the MNIST dataset
- Regarding performance of different methods for addressing imbalance, in almost all of the situations oversampling emerged as the best method.  
- Undersampling showed overall poor performance 
- Two phase training methods with both undersampling and oversampling tend to perform between the baseline and their corresponding method (undersampling or oversampling)

#### Methods for addressing imbalance (data level methods vs. algorithmic level methods)
- **Data Level Methods**
  - *Oversampling*: Most commonly used method.  Basic version of it simply replicates randomly selected samples from minority classes.  Effective, but can lead to overfitting
  - *Undersampling*: Examples are removed from the majority class.  Significant disdainantage of this method is that it disregards available data 
- **Classifier Level Methods**
  - *Thresholding*: Adjusts the decision threshold of a classifier.  Applies in the test phase and involves changing the output class probabilities 
  - *Cost sensitive learning*: Method assigns different cost to misclassification of examples from different classes.  One approach is thresholding/post scaling applied in the inference phase after the classifier is already trained.  Finally we can train the network by minimizing the misclassification cost instead of standard loss function
  - *One-class classification*: In the context of NN’s it is usually called novelty detection.  Concept learning technique that recognizes positive instances rather than discriminating between two classes

### Conclusions
- As opposed to some classical machine learning models, oversampling does not necessarily cause overfitting of convolutional neural networks

