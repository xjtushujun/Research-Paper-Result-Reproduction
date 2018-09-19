# Evasion attacks against machine learning at test time : [1708.06131](https://arxiv.org/pdf/1708.06131.pdf)
## Desired proactive protection mechanisms
(i) finding potential vulnerabilities of learning before they are exploited by the adversary; 
(ii) investigating the impact of the corresponding attacks (i.e., evaluating classifier security); 
(iii) devising appropriate countermeasures if an attack is found to significantly degrade the classifier’s performance


General approach is to use Game-theory approach attacker vs defense till it reaches Nash equilibrium. but realsitic constaints are too hard to be incorporated into game theory
## Adversary’s goal: 
* Adversary’s goal should be defined in terms of a utility (loss) function that the adversary seeks to maximize (minimize). 
* In the evasion setting, the attacker’s goal is to manipulate a single (without loss of generality, positive) sample that should be misclassified.

## Adversary Knowledge (Attackers Knowledge about the system,):
* the training set or part of it;
* the feature representation of each sample; i.e., how real objects such as emails, network packets are mapped into the classifier’s feature space;
* the type of a learning algorithm and the form of its decision function;
* the (trained) classifier model; e.g., weights of a linear classifier;
* or feedback from the classifier; e.g., classifier labels for samples chosen by the adversary.

## Adversary’s capability.: 
 In the evasion scenario, the adversary’s capability is limited to modifications of test data; i.e.altering the training data is not allowed.
However, under this restriction, variations in attacker’s power may include:
* modifications to the input data (limited or unlimited);
* modifications to the feature vectors (limited or unlimited);
* or independent modifications to specific features (the semantics of the input data may dictate that certain features are interdependent).


## Attack Scenarios : 
Perfect knowledge (PK) --> The adversary knows the feature space, the type of the classifier, and the trained model.he adversary can transform attack points in the test data but must remain within a maximum distance of dmax from the original attack sample. Dmax constraint is added to make sure the semantic meaning from the real data is not lost. 
Limited knowledge (LK). The attacker knows the feature representation and the type of the classifier, but does not know either the learned classifier f  or its training data  D , and hence can not directly compute  g(x). But the advesary has access to surrogate dataset D' from the same underlying distribution as D. This can be done by sniffing some network traffic during the classifier operation, or by collecting legitimate samples from alternate source.  Under this scenario , we try to approximate\mimic the original classifier by trainning on the surrogate dataset with similar settings. Amount of Surrogate data is a attack hyper parameter .

well-known techniques, like gradient descent, or quadratic techniques such as Newton’s method, BFGS, or L-BFGS can be used to optimize this non linear optimization problem 

when using gradient descent approach on non convex problems, we don't have guarantee to arrive at global minima always. Hence at local minima the performance of the adversary will be poor and may not evade depending on the behavior of g(Approximated Function). To Overcome the effect/possiblity of local minima we add a λ* penalizer KDE (Kernel Density Estimator )  with bandwidth h. a.k.a (mimicry component.)
The extra component favors attack points that imitate features of known legitimate samples. Which in turn  reshapes the objective function and thereby biases the resulting gradient descent towards regions where the negative class is concentrated 

## Gradient descent attacks -- 
# TO DO :
Section 3 Redo : pseudo code to python translate 

 the gradient of kernel density estimators depends on the kernel gradient.

TLDR :  
