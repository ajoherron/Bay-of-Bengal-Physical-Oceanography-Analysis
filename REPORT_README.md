# 1004 Final Project: Collaborative-Filter Based Recommender System

Group 70 
- Alex Herron (ah5865)
- Dhruv Saxena (ds6802)
- Sukrit Rao (sr8775)

Link to our repository: [Group 70 repository](https://github.com/nyu-big-data/final-project-group_70)

## **Implementation:**

## 1. Data partitioning:

To split the data into train / test / validation sets, we first split 70% of the total observations into the training set. Specifically, we included 70% of the data from each user, in order to guarantee that there would be sufficient training observations for the recommender system to learn each user's preferences. Without ensuring that each user's ratings appeared in the training set, the model would need to randomly evaluate users who's ratings were excluded from the training set.

Next, we split the remaining 30% of total observations into validation and test sets, which were split by user. For this, we randomly split all the users into two groups (let's say group A and group B), then split those groups of users into validation and test sets. Because different users reviewed a different number of movies, the 30% is not perfectly split into 15% validation and 15% test. For example, users in group A might review, on average, more movies that users in group B. However, since the datasets are so large, the validation and test splits end up being generally close to 15% of the total observations.

## 2. Popularity baseline model

For the baseline model, we calculated average ratings for each movie. These averaged ratings served as the predicted rating for each given user. Moving forwards, this serves as a useful baseline, since we can now compare a collaborative-filter based model to a model that simply predicts the average rating of a movie for all users. It is safe to say that, if a recommender system cannot perform better than averaged ratings, it is most likely not a great recommender system.

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

LightFM Test Scores - Small Data

Fraction | Count | Time Taken | Precision_at_100
--- | --- | --- | --- |
0.1 |	7194.0 |	0.06469202041625977 |	0.06558219343423843
0.2 |	14388.0 |	0.09870481491088867 |	0.06835051625967026
0.30000000000000004 |	21582.0 |	0.14845609664916992 |	0.07261168211698532
0.4 |	28776.0 |	0.13022899627685547 |	0.0754639133810997
0.5 |	35970.0 |	0.14635515213012695 |	0.07652921229600906
0.6 |	43163.0 |	0.1635723114013672 |	0.07735395431518555
0.7000000000000001 |	50357.0 |	0.1778271198272705 |	0.07914088666439056
0.8 |	57551.0 |	0.18615484237670898 |	0.08175258338451385
0.9 |	64745.0 |	0.24546480178833008 |	0.08103092759847641
1.0 |	71939.0	| 0.23988103866577148 |	0.0821649506688118

LightFM Test Scores - Large Data

Fraction | Count | Time Taken | Precision_at_100
--- | --- | --- | --- |
0.1	| 1984562.0 |	182.62801003456116 | 0.06218128278851509
0.2 | 3969124.0 |	228.26030683517456 | 0.06998410820960999
0.30000000000000004 |	5953686.0 | 301.34373712539673 | 0.07340791076421738
0.4 |	7938248.0 | 265.50041604042053 | 0.0751897469162941
0.5 |	9922810.0 | 283.1478729248047 | 0.07705644518136978
0.6 |	11907371.0 | 292.629301071167 | 0.07831323891878128
0.7000000000000001 | 13891933.0 | 308.4834396839142 | 0.07824498414993286
0.8 |	15876495.0 | 321.8523201942444 | 0.07848569750785828
0.9 |	17861057.0 | 375.8229920864105 | 0.08090633153915405
1.0 |	19845619.0 | 343.4911799430847 | 0.08004886656999588

## 7. 2nd Extension: NEED TO FIGURE OUT WHICH TO DO
