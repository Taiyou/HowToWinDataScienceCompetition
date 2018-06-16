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






