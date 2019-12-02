# Machine Learning Project 

**Introduction**

Pulse shape discrimination (PSD) is a method for separating the pulses from different particles. For distinct pulses, the classical methods are good enough to separate the pulses. However, for similar pulses, the classical PSD methods are not very effective. In those cases, machine learning methods could be used to effectively classify the particles.  In this project, I will try to reproduce the result of Zhang et al. [1] which uses support vector machine (SVM) for PSD. SVM is also used by Sanderson et al. [2] and Yu et al. [3] for  the PSD.


**Original Paper Summary**

Zhang et al. [1] describes a method to classify nuclear pulses using principal component analysis (PCA) and support vector machine (SVM). Even the pulses which are similar to naked eye, could be classified with accuracies greater than 94.7%.

The pulses from 9 different circuit boards are grouped in three groups, each consisting of three kinds of pulses. The pulses consists of 1000 dimensions, in which PCA is applied and are transformed into 2 dimensional space. After PCA transformation two groups shows a clear separation of pulses while the third group does not show a clear boundary. After PCA processing each group is trained with SVM learners. The training and testing accuracies for linear, quadratic, cubic and gaussian kernels are compared. 

The PSD method based on PCA and SVM is effective and simple for particle identification.

**Procedure**

My research data consists of the digitized pulses from gammas and neutrons. Gamma and neutron are two different kinds of particles with slightly different pulse shape in our detector. The pulse from the detector has 129 samples of analog to digital converter.

I made two groups of data with three types of pulses in each group. The first group consists of the strong-gamma, weak-gamma, and strong-neutron; The pulses with higher pulse height are categorized as strong and the pulse with lower pulse height are called weak. I took 10,000 pulse samples from each types of pulses, with a total of 30,000 pulse samples. I made the second group with weak-gamma, weak-neutron, and strong-neutron. This group also has 30,000 total pulses, 10,000 each for three kinds of pulses.

I used scikit-learn [4] to implement the algorithms. First, I used PCA to reduce 129 dimensional data into 2 dimensions and visualized it. For the pulses in group 1, PCA shows a clear separation of the data as shown in the figure 1. However in group 2, weak-gamma and weak-neutron are not separable from each other. Then I trained and tested four SVM classifier with linear, quadratic, cubic, and gaussian kernels. The training and testing accuracies are summarized in table 1.

![both_plot](https://user-images.githubusercontent.com/53912470/69448945-afa60480-0d27-11ea-8365-63307b5e40e9.jpg)

Figure 1: 2 component PCA for group 1 and group 2


Table 1: Training/testing accuracies of SVM with different kernels (%)

| Group       | Linear Kernel          | Quadratic Kernel  | Cubic Kernel | Gaussian Kernel |
| ------------- |-------------| -----|-------|----------|
| 1      | 100/100 | 99.99/99.96 | 99.97/99.97 | 100/99.97 |
| 2      | 99.98/99.87      |   96.44/96.02 | 98.62/98.17 | 99.91/99.90 |

**Result and Discussion**

Both the training and testing accuracies for all types of kernels are greater than 96% which verifies the finding of the original paper. The linear kernel has highest training and testing accuracy for both groups of data. This is different than that of the original paper, in which not a single kernel gives best performance for all groups.
Hence, I verified the finding of the original paper with some minor differences. These differences might be due to the different kind of datasets.

**References**

[1] Zhang, Z. H., et al. "A direct method of nuclear pulse shape discrimination based on principal component analysis and support vector machine." Journal of Instrumentation 14.06 (2019): P06020.

[2] Sanderson, T. S., et al. "Machine learning for digital pulse shape discrimination." 2012 IEEE Nuclear Science Symposium and Medical Imaging Conference Record (NSS/MIC). IEEE, 2012.

[3] Yu, Xunzhen, et al. "Neutron–gamma discrimination based on the support vector machine method." Nuclear Instruments and Methods in Physics Research Section A: Accelerators, Spectrometers, Detectors and Associated Equipment 777 (2015): 80-84.

[4] Pedregosa, Fabian, et al. "Scikit-learn: Machine learning in Python." Journal of machine learning research 12.Oct (2011): 2825-2830.
