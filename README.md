# A survey on BATADAL dataset




## Introduction

This survey consists of the following part.

    `--` Brief introduction on BATADAL dataset. 

    `--` A summary of other researchers' work on BATADAL dataset.

    `--` The record of my experimental details and results.




## Dataset

BATADAL dataset is a multivariate time series dataset for anomaly detection in the context of water distribution system. 

This dataset is proposed in the publication below.

***Taormina R, Galelli S, Tippenhauer N O, et al. Battle of the Attack Detection Algorithms: Disclosing cyber attacks on water distribution networks[J]. Journal of Water Resources Planning and Management, 2018, 144(8).***

Details of this dataset can be found here https://github.com/scy-phy/www.batadal.net and here http://www.batadal.net/




## Summary of researches on BATADAL dataset


After that the water distribution systems(WDS) have upgraded from physical systems into cyber-physical systems, WDS is more vulnerable and susceptible to cyber attacks. More specifically, the element named supervisory control and data acquisition systems(SCADA) makes WDS more vulnerable to attacks. Hence there are more needs for developing powerful and reliable cyber-attack detection techniques or systems. Cyber-attacks detection techniques are either model-driven or data-driven.



### BATADAL competition

Here comes the research teams who took the BATADAL competition and introduction of their papers. The results of these research teams can be found on the official website of BATADAL. http://www.batadal.net/results.html


1. Housh et al.

***Model-based approach for cyber-physical attack detection in water distribution systems***

Model-driven approach. Firstly estimate the demand based on partial SCADA readings. Secondly simulate the hydraulics based on the estimated demand using *EPANET*, a physically based water hydraulics simulation model. Next calculate the errors between SCADA readings and simulated values. Finally find anomalies through applying moving average and decision rules on errors.


2. Abokifa et al.

***Detection of Cyber Physical Attacks on Water Distribution Systems via Principal Component Analysis and Artificial Neural Networks***

Data-driven method. 3 layers framework. The first layer is to detection anmalies from statistical perspective using mean and standard deviation. The second is multi-layer perceptron(MLP) used to detect contextual anomalies. The input data is noisy so FFT and third degree low pass Butterworth filter are applied to input data before being fed to MLP. The third layer is PCA, tranforming the principal components into 2 subspaces, normal subspace(the first 14 principal components) and anomaly subspace(the rest). Besides directly applying PCA, the authors also implement leave out one(LOO) algorithm which adds instances of interest to the data to see if it changes the direction of princial components.

In 2018, Abokifa et al. make some improvement on his previous aforementioned work. The improvement is illustrated in the paper ***Real-Time Identification of Cyber-Physical Attacks on Water Distribution Systems via Machine Learning Based Anomaly Detection Techniques***. They refine their idea from the following perspectives, 
    a. they add one more module named actuator rules verification which is similar with other rule-based approach. 
    b. they apply semi-supervised learning structure, adding the data that is predicted to be normal to the trusted dataset to retrain the model.
    c. Alarm watch window.


3. Giacomoni et al.

***Identification of Cyber Attacks on Water Distribution Systems by Unveiling Low-Dimensionality in the Sensory Data***

Data-driven and Convex optimization-based approach.
The first step of the algorithm is to apply actuator rule verification and data verification(some rules set manually to identify whether the system is under attack). If there is no anomaly reported after the first step, then apply optimization-based detection algorithm to detect attacks further.


4. Brentan et al.

***On-line cyber attack detection in water networks through state forecasting and control by pattern recognition***

Data-driven approach. Apply NARX model to predict the future state of the water distribution system. And then for a series error terms which are obtained by computing the difference between prediction and measured data,  use standard deviation of error terms to detect possible anomalies.


5. Chandy et al.

***Detection of cyber-attacks to water systems through machine-learning-based anomaly detection in scada data***

Data-driven approach. Machine learning methodology, comprised of 2 parts. The first part is rule-based method, checking if the operation/physical rules are broken. It's a bit like the verification step in the algorithm proposed by Giacomni et al. The second part is used to confirm the flagged events. It's composed of a convolutional variational autoencoder. Autoencoder is trained on normal data. Given a new data point, we can determine whether it's an anomaly by the reconstruction probability. 

In 2018, Chandy et al. refined their work by only using variational autoencoder and discarding the rule-based part in their previous work. The refinement is elaborated in the paper ***Cyberattack Detection using Deep Generative Models with Variational Inference***.


6. Posha et al.

***An approach to detect the cyber-physical attack on water distribution system***

Data-driven approach. The method consists of 3 modules. The first one is to check if the data point is consistent with the control rules. The second one is pattern recognition. The model is trained on normal data to define normal behavior patterns. The third one is developed based on the relationships between the components of water distribution systems. This part is for confirming the attack events detected by the aforementioned modules.


7. Aghashahi et al.

***Water distribution systems analysis symposium-battle of the attack detection algorithms (BATADAL)***

Data-driven approach. The algorithm is composed of 3 steps. The first is to preprocess the data(remove the time and flag). The second is to train a random forest. Here is how they get input training data ready. Firstly compute average lag-0 covariance matrix A(31,31) for normal series and average lag-1 covariance matrix B(31,31) for anomalous series. Then for a time point t, compute lag-0 covariance matrix C(31,31) for it. Finally the distance measure(input for RF) is (norm of C-A, norm of C-B). The third step is to test the model.



### Other researches on BATADAL dataset

In this section, some other researches using BATADAL dataset is shown below. Although these research teams didn't participate in the competition, their work has something to do with BATADAL dataset


1. Abdulaziz Almehmadi.

Treat the intrusion detection task as binary classification. The author firstly extract some features from SCADA readings manually and then apply PCA to select some crucial features. Finally train Naïve bayes, svm and random forest separately to see which algorithm performs the best. And random forest can mitigate the impact that imbalanced data has so it performs the best compared with naïve bayes and svm.


2. Erba et al.

They proposed white box and black box attack algorithms to evade detection of the system. It's an very interesting work. As for white box, since the assumption is attackers know how detection system is performed, they modify some variables of the anomalous data in order to craft hard-to-recognize anomalies. As for black box, they use adversarial trained autoencoder to generate anomalies with pertubations. Also, They re-create a dataset from BATADAL dataset so as to add concealment themselves.
	
