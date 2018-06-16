# Ensemble
## bagging
means averaging slightly different version of the same model to improve accuracy.
## Why bagging
There are 2 main sources of errors in modelling:
1. errors due to Bias
2. Errors due variance
## parameters that control bagging?
- changing the seed
- row sampling or bootstrapping
- shuffling
- column sampling
- model-specific parameters
- number of models (or bags)
- parallelism

## examples of bagging
- BaggingClassifier and BaggingReggressor from sklean.

# Boosting
## What is boosting?
a form of weighted averaging of models where each model is built sequentially via taking into account the past model performance.

## Main boosting types
- weight-based
- 

## weight based boosting
add weight which indicates 

## weight based boosting parameters
- learning rate (or shrinkage or eta
- we trust a model a bit, but not 100%.
- number of estimators, usually hard to get but with cross-validation

## Weight-based boosting parameters
- learning rate
- number of estimators
- input model- can be anything that accepts weight
- sub boosting type:
 1. AdaBoost: Good implementation in sklearn
 2. LogitBoost: good implementation in Weka

## Residual based boosting
we calculate the difference between predict and actual balue.
we finally predict based on 1st and 2nd predictions

## Residual based boosting parameters
- learning rate ( chrinkage or eta
- number of estimators
- Row and column sampling
- input model - better be trees.
- sub boosting type:
1. fully gradient based
2. Dart

## Residual based favourite implementations
- Xgboost
- Lightgbm
- H2O's GBM
- Catboost
- SKlearn's GBM

# Stacking
means making predictions of a number of models in hold-out set and then using a different model to train these predictions.
## methodology
- Wolpert in 1992 introduced stacking. it involves:
1. Splitting the train set into two disjoint sets.
2. train several ased learners on the first part.
3. make predictions with the base learners on the second part
4. using the predictions from (3) as the input train a higher level learner.

## Still confused about stacking?
train algorith 0-2 on A and make predictions for B and C and save t B1, C1

## Stacking example
## Things to be mindful of
- with time sensitive data - respect time
- diversity as important as performance
- diversity may come from:
1. different alogorithms
2. different input features
- performance plateauing after N models
- meta model is normally modest

# StackNet
A scalable meta modelling methodology that utilizes 
stacking to combine multiple models in a neural network architecture of multiple levels.

## Naive example
- stacking multiple meta models

## Why would this be of any use?
- 3-level stacking in homesite
## STackNet as a neurla network
- in a neurla network, every node is a simple linear model with some non-linear transformation.
- instead of a linear model we could use any model.

## How to train
- we cannot use BP ( not all models are differentiable
- we use stacking to link each model/node with target.
- to extend to many levels, we can use a Kfold paradigm.
- No epochs -different connections instead.

- cons: larger number of data is needed.

# ensembling tips and tricks 
## 1st level tips
- diversity based on algorithms
1. 2-3 gradient boosted trees )lightgb, xgboost, H2o
2. 2-3 neural nets ) kera, pytorch
3. 1-2 extra trees/ random forest
4. 1-2 linear model as in logistic/ridge regression, linear svm
5. 1-2 knn models
6. factorization machine 
7. svm with nonlinear kernel if size/memory allows
- diversity based on input data
1. categorical features: one hot, label encoding, target encoding
2. numerical features: outliers, binning, derivatives, percentiles, scaling
3. interactions: col1(/-col2, groupby, unsupervised

## subsequent level tips
- simpler algorithms:
1. gradient boosted trees with small depth
2. linear models with high regularizationabout
3. extra trees
4. shallow networks
5. knn with BrayCurtis Distance
6. Brute forcing a search for best linear weights based on cv
- Feature engineering:
1. pairwise differences between meta features
2. row-wise statistis like averages or stds
3. standard feature selection techniques
- For every 7.5 models in previous level we add 1 in meta
- be mindful of target leakage.

## Software for stacking
- StackNet 
- stacked ensembles from H2O
- Xcessiv

## Tips about StackNet
- it supports many prominent tools
- can run classifiers in regression and vice versa.-
- It has several top 10s in comeptitions.

## Before we say goodbye...
- apply what you have learnt
- it takes some time to adjust.
- Always save your code and re-use it
- seek collaborations
- read forums/kernels

# Quiz
[Stacking Schema](https://www.coursera.org/learn/competitive-data-science/supplement/JThpg/validation-schemes-for-2-nd-level-models)
## Q1 Suppose we are given a train set and test set, that came from the same distribution. We want to use stacking and choose between the validation schemes described in the reading material.
- Scheme d) is less efficient from computational perspective than scheme a). That is, if a dataset is very large, scheme a) is usually preferred over scheme d).
- Scheme e) gives the validation score with the least variance, if compared to schemes a) -- d).
## Q2 Definition: we will call a validation scheme fair if the set, that we use to validate meta-models comes from the same distribution as the meta-test set. In other cases we will call validation scheme leaky. In other words in a fair validation scheme the set that we use to validate meta-models was not used in any way during training first level models.
Select fair validation schemes. 

## Q3. Which of the following ensembling methods can potentially learn "conditional averaging" (video 1)?
- Bagging
- Boosting on trees
## Q4. The benefits of the weighted average compared to more advanced ensembling techniques is that

## Q5. In general case, which set of base models is probably the best for stacking?
[Logistic Regression, SVM, Random Forest, Extra Trees Classifier, GBDT]
## Q6. Suppose we are given a classification task. In a simple two model linear mix we usually use weights \alphaα for the first model and \betaβ for the second one. The coefficients are usually chosen such that \alpha + \beta = 1α+β=1, because convex combination of probability vectors is a probability vector. Still, sometimes it is beneficial to tune \alphaα and betabeta independently, e.g. mix with \alpha=0.1α=0.1 and \beta=0.8β=0.8 works best. However, for some metrics it never makes sense to tune \alphaα and \betaβ independently. That is, searching for independent \alphaα and \betaβ will never give you better results than searching for weights, constrained to be \beta = 1 - \alphaβ=1−α. Select such metrics.
- AUC
- Accuracy
