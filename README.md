# Machine Learning Project 

**Original Paper Summary**

For similar pulses, the classical pulse shape discrimination (PSD) methods are not very effective. This paper describes a method to classify nuclear pulses using principal component analysis (PCA) and support vector machine (SVM). Even the pulses which are similar to naked eye, could be classified with accuracies greater than 94.7%.

The pulses from 9 different circuit boards are grouped in three groups, each consisting of three kinds of pulses. The pulses consists of 1000 dimensions, in which PCA is applied and are transformed into 2 dimensional space. After PCA transformation two groups shows a clear separation of pulses while the third group does not show a clear boundary. After PCA processing each group is trained with SVM learners. The training and testing accuracies for linear, quadratic, cubic and gaussian kernels are compared. 

The PSD method based on PCA and SVM is effective and simple for particle identification.

**Procedure**

My research data consists of the digitized pulses from gammas and neutrons. Gamma and neutron are two different kinds of particles with slightly different pulse shape in our detector. The pulse from the detector has 129 samples of analog to digital converter.

I made two groups of data with three types of pulses in each group. The first group consists of the strong-gamma, weak-gamma, and strong-neutron; The pulses with higher pulse height are categorized as strong and the pulse with lower pulse height are called weak. I took 10,000 pulse samples from each types of pulses, with a total of 30,000 pulse samples. I made the second group with weak-gamma, weak-neutron, and strong-neutron. This group also has 30,000 total pulses, 10,000 each for three kinds of pulses.

I used scikit-learn [\cite] to implement the algorithms. First, I used PCA to reduce 129 dimensional data into 2 dimensions and visualized it. For the pulses in group 1, PCA shows a clear separation of the data as shown in the figure \ref. However in group 2, weak-gamma and weak-neutron are not separable from each other. Then I trained and tested four SVM classifier with linear, quadratic, cubic, and gaussian kernels. The training and testing accuracies are summarized in table \ref.

Training/testing accuracies of SVM with different kernels (%)

| Group       | Linear Kernel          | Quadratic Kernel  | Cubic Kernel | Gaussian Kernel |
| ------------- |-------------| -----|-------|----------|
| 1      | 100/100 | 99.99/99.96 | 99.97/99.97 | 100/99.97 |
| 2      | 99.98/99.87      |   96.44/96.02 | 98.62/98.17 | 99.91/99.90 |

**Result**

Both the training and testing accuracies for all types of kernels are greater than 96% which verifies the finding of the original paper. The linear kernel has highest training and testing accuracy for both groups of data. This is different than that of the original paper, in which not a single kernel gives best performance for all groups.
Hence, I verified the finding of the original paper with some minor differences. These differences might be due to the different kind of datasets.

**References**

Pedregosa, Fabian, et al. "Scikit-learn: Machine learning in Python." Journal of machine learning research 12.Oct (2011): 2825-2830.
