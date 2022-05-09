# 1004 Final Project - Recommender System

Group 70 
- Alex Herron (ah5865)
- Dhruv Saxena (ds6802)
- Sukrit Rao (sr8775)

Link to our repository: [Group 70 repository](https://github.com/nyu-big-data/final-project-group_70)

## **Implementation:**

## 1. Data partitioning:

To split the data into train / test / validation sets, we first split 70% of the total observations into the training set. Specifically, we included 70% of the data from each user, in order to guarantee that there would be sufficient training observations for the recommender system to learn each user's preferences.

Next, we split the remaining 30% of total observations into validation and test sets, which were split by user. For this, we randomly split all the users into two groups, then split those groups of users into validation and test sets. Because different users reviewed a different number of movies, the 30% is not perfectly split into 15% validation and 15% test. However, since the datasets are so large, both values end up being generally close to 15% of the total observations.

## 2. Popularity baseline model

For the baseline model, we calculated average ratings for each movie. Moving forwards, this will serve as a useful baseline. It is safe to say that, if a recommender system cannot perform better than averaged ratings, it is most likely not a great recommender system.

## 3. Alternating Least Squares

For the ALS model, we fit our model on the training set for **10 epochs** using a **regularization parameter of 0.01** and **latent factor rank of 10**. This setting was used for both the small and large datasets. Future work includes performing hyperparameter tuning to find the optimum values of the before-mentioned parameters. 

## 4. Hyperparameter tuning

For our hyperparameter tuning, we sought to find the combination of hyperparameters (including the rank (dimension) of the latent factors, and the regularization parameter) that produced the best results. We defined this “best result” as whatever combination of rank and regularization parameter obtained the **highest precision at k** (for which we used k = 100).

In order to accomplish this, we used scipy.optimize.fmin, which uses a Nelder-Mead simplex algorithm that uses function values to determine which parameters minimize a given objective function. Using fmin, we determined that the optimal hyperparameters for maximizing our precision at k are:
**Optimized rank = ???**
**Optimized regularization parameter = ???**

## **Evaluation:**

## 5. Evaluation

For our baseline model, we calculated the following metrics:

Metric | Small Data | Large Data |
--- | --- | --- |
Precision at 100 | 0.00039344262295081965 | 1.503495623335514-06 |
Mean average precision | 0.0001430963103190941 | 3.2435290469904e-08 |
Normalized discounted cumulative gain | 0.0007401952547559103 | 1.5366084699026787e-06 |

For the untuned ALS model (trained, validated, and tested using the **small data**), we calculated the following metrics:

Untuned ALS - Small Data | Validation | Test |
--- | --- | --- |
Root mean square error | 1.1752318331139788 | 1.1485114835373875 |
Precision at 100 | 0.015868852459016397 | 0.0014954161283035237 |
Mean average precision | 0.001450805120152909 | 0.014524590163934429 |
Normalized discounted cumulative gain | 0.022022188555771365 | 0.019983620211370335 |

For the untuned ALS model (trained, validated, and tested using the **large data**), we calculated the following metrics:

Untuned ALS - Large Data | Validation | Test |
--- | --- | --- |
Root mean square error | ? | ? |
Precision at 100 | ? | ? |
Mean average precision | ? | ? |
Normalized discounted cumulative gain | ? | ? |

In constrast, for the tuned ALS model (which used our optimized values for rank and regularization parameter), we calculated the following metrics for the **small data**:

Tuned ALS - Small Data | Validation | Test |
--- | --- | --- |
Root mean square error | ? | ? |
Precision at 100 | ? | ? |
Mean average precision | ? | ? |
Normalized discounted cumulative gain | ? | ? |

Additionally, for the tuned ALS model (which used our optimized values for rank and regularization parameter), we calculated the following metrics for the **large data**:

Tuned ALS - Large Data | Validation | Test |
--- | --- | --- |
Root mean square error | ? | ? |
Precision at 100 | ? | ? |
Mean average precision | ? | ? |
Normalized discounted cumulative gain | ? | ? |

## **Extensions:**

## 6. 1st Extension: lightfm

## 7. 2nd Extension: ???
