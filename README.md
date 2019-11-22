# Machine Learning Project 

#Original Paper Summary
For similar pulses, the classical pulse shape discrimination (PSD) methods are not very effective. This paper describes a method to classify nuclear pulses using principal component analysis (PCA) and support vector machine (SVM). Even the pulses which are similar to naked eye, could be classified with accuracies greater than 94.7%.

The pulses from 9 different circuit boards are grouped in three groups, each consisting of three kinds of pulses. The pulses consists of 1000 dimensions, in which PCA is applied and are transformed into 2 dimensional space. After PCA transformation two groups shows a clear separation of pulses while the third group does not show a clear boundary. After PCA processing each group is trained with SVM learners. The training and testing accuracies for linear, quadratic, cubic and gaussian kernels are compared. 

The PSD method based on PCA and SVM is effective and simple for particle identification.

Procedure
My research data consists of the digitized pulses from gammas and neutrons. Gamma and neutron are two different kinds of particles with slightly different pulse shape in our detector. The pulse from the detector has 129 samples of analog to digital converter.

I made two groups of data with three types of pulses in each group. The first group consists of the strong-gamma, weak-gamma, and strong-neutron; The pulses with higher pulse height are categorized as strong and the pulse with lower pulse height are called weak. I took 10,000 pulse samples from each types of pulses, with a total of 30,000 pulse samples. I made the second group with weak-gamma, weak-neutron, and strong-neutron. This group also has 30,000 total pulses, 10,000 each for three kinds of pulses.
