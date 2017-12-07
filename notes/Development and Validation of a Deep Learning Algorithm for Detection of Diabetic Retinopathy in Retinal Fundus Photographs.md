## Development and Validation of a Deep Learning Algorithm for Detection of Diabetic Retinopathy in Retinal Fundus Photographs

##### **V. Gulshan, L. Peng, M. Coram, M. C. Stumpe, D. Wu, A. Narayanaswamy, S. Venugopalan, K. Widner, T. Madams, J. Cuadros, R. Kim, R. Raman, P. C. Nelson, J. L. Mega, D. R. Webster (2016)**

Summary: The objective of this paper is to create an algorithm for detection of DR and DME in retinal fundus photographs.  The sensitivity and specificity of the algorithm for detecting RDR, defined as moderate and worse DR, RDME, or both, were generated based on the reference standard of the majority decision of the ophthalmologist panel.  The graders for the dev set were US-licensed ophthalmologists or ophthalmology trainees in their last year of residency.  

### Definitions
- **ROC Curve**: Curve created by plotting the TPR against the FPR at various threshold settings.   
- **Sensitivity**: Measures the proportion of positives that are correctly identified as such (TPR)
- **Specificity**: Measures the promotion of negatives that are correctly identified as such (TNR)
- **TPR**: Sensitivity 
- **FPR**: 1 - Specificity

### Notes 
-  The function computes DR severity form the intensities of the pixels in a fundus images
- The NN used was the Inception-v3-architecture
- To speed up the training, batch normalization as well as preinitialization were used 
- The optimization algorithm used to train the network used to train the network weights was a distributed SGD implementation
- A single network was trained to make multiple binary predictions, including whether the image was (1) moderate or worse 
DR (ie, moderate, severe, or proliferative), (2) severe or worse DR, (3) RDME, or (4) fully gradable
- RDR was defined as any image that satisfied criterion 1, criterion 3, or both 
- The trained NN generates a continuous number between 0 and 1 for RDR and other DR classifications, corresponding to the 
probability of that condition
- ROC curves were plotted by varying the operating threshold and 2 operating points for the algorithm were selected from the 
development set
- The team also performed experiments to understand the relationship between the amount of development data on the 
performance of the resulting algorithms

### Results
- For RDR, the algorithm achieved an AUC of .991 on EyePACS-1 and an AUC of .990 on Messidor-2 
- Using the first operating cut point with high specificity, approximating the specificity of opthalmologists in the dev set, 
on EyePACS-1, the algorithm’s sensitivity was 90.3% and specificity was 98.1%.  In Messidor-2, the sensitivity was 87.0% 
and specificity was 98.5%
- A second operating point for the algorithm was evaluated, which had a high sensitivity on the development set.  Using this operating point, on EyePACS-1, the algorithm had a sensitivity of 97.5% and a specificity of 93.4%.  In Messidor-2, the sensitivity was 96.1% and the specificity was 93.9%


### Datasets 
For algorithm development, macula centered retinal funds images were retrospectively obtained from EyePACS-1 in the US and 
3 eye hospitals in India.  All images were de-identified prior to transfer to study investigators.  Two more datasets were 
used for clinical validation.  Namely the Messidor-2 dataset, and a random sample of images from the EyePACS-1 dataset.  
