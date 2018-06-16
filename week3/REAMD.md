# Week3
## Statistics and distance based features
eg. some data for CTR task
- user_id, page_id, ad_price, ad_position
- useful features, 
- user_id, page_id, Ad_price, Ad_position, max_price, min_price, min_price_position

## More features
- how many pages user visited
- standard deviation of prices
- most visited page
- many, many more.

## Neighbors
- explicit group is not needed
- more flexible
- much harder to implement
1. number of houses in 500m, 1000m...
2. average price per square meter in 500m, 1000m
3. number of schools/supermarkets/praking lots in 500m, 1000m
4. distance to closet subway station

## KNN features in Springleaf
- mean encode all the variables
- For every point, find 2000 nearest neighbors using Bray-Curtis metric.
- calculate various features from those 2000 neighbors.
1. Mean target of nearest 5,10,15,500,2000 neighbors
2. mean distance to 10 closest neighbors
3. Mean distance to 10 closest neighbors with target1
4. Mean distance to 10 closest neighbors with target0.

## Matrix factorization for feature extraction
- Can be applied only for some columns
- Can provide additional diversity
1. good for ensembles
- It is a lossy transformation. It's efficiency depends on:
- particular task
- number of latent factors
1. usually 5-100.

## Implementationcan 
- several MF methods you can find in sklearn
- SVD and PCA
1. standard tools for matrix factorization
- Truncated SVD
2. works with sparse matrices
- Non-negative matrix factorizatoin (NMF
3. ensures that all latent factors are non-negative
4. good for counts-like data

## NMF for tree-based method
## Notes about MF
- Matrix factorization is similar in sprit to linear models.
- you can use the same transformation tricks.

## Gochas
- Right way:
- split train and test data
- apply PCA to split data separately.

## Conclusion
- Matrix factorization is a very general approach fordimensionality reduction and feature extraction.
- It can be applied for transforming categorical features into real-valued
- Many of tricks suitable for linear models can be useful for MF.

## Feature interaction
## banner selection
- category_ad, category_site, is_cliched
new feature
- ad_site, is_clicked

## example of interactions
- multiplication, sum, diff, division

## Practical Notes
- We have a lot of possible interactions - N*N for N features
a. even more if use several types in interactions
- need to reduce it's number 
a. dimensionality reduction
b. feature selection

## interaction generation pipeline
1. data
2. feature extraction
3. fit random forest, get feature importances, select a few most important

## interactions' order
- we looked at 2nd order interactions
- such approach can be generalized for higher orders.
- It is hard to do generation and selection automatically.
- Manual building of high-order interactions is some kind of art.

## conclusion
1. We looked at ways to build an interaction categorical attributes
2. Extended this approach to real-valued features
3. Learn how to extract features via decision trees.

## tSNE
- manifold learning methods.
## Practical Notes
- result heavily depends on hyperparameters
1. good practice is to use several projections with different perplexities
- due to stochastic nature, tSNE provides different projections even for the same data hyper params
2. train and test should be projected together
- tSNE runs for a long time with a big number of features
3. it is common to do dimensionality reduction before projection.

# Quiz
## Quiz1. Imagine that we apply X = PCA(n_components=5).fit_transform(data) and data has shape (5000, 53). What is the shape of X?
## Answers: 5000, 5

## Quiz2. To which data NMF is NOT applicable?
- Bag-of-words matrix
- standartized matrix
- one-hot encoded featured
## Answers: standartized matrix

## Quiz 3. Suppose we have 2 categorical features: f1 with A possible values and f2 with B possible values. How many values will their interaction have?
- exactly A + B
- exactly A*B
- less or equal to A*B
- max(A,B)
## Answers:  less or equal to A*B

## Quiz 4; Imagine we have 2 categorical features represented as integers: f1 with all values in range [0, 1000] and f2 with values in range [0, 100]. What is the correct way to build their interaction?
- f1 + f2
- f1.astype(str) + f2.astype(str)
- f1.astype(str) + "_" + f2.astype(str)
- (f1 + f2).astype(str)
## Answers: 

## Q5. What is a correct way to get t-SNE projection of train and test data?
- Apply t-SNE to concatenation of train and test and split projection back.
## Answers: 
## Q6. Is it possible to do t-SNE projection into 20 dimensional space
- Yes, why not?

## additional materials
### Matrix factorization:
- [Overview of Matrix Decomposition methods](http://scikit-learn.org/stable/modules/decomposition.html)
### t-SNE:
- [multicore t-SNE implementation](https://github.com/DmitryUlyanov/Multicore-TSNE)
- [comparison of manifold learning methods](https://github.com/DmitryUlyanov/Multicore-TSNE)
- [how to uuse t-SNE effectively](https://distill.pub/2016/misread-tsne/)
- [tSNE homepage](https://lvdmaaten.github.io/tsne/)
### interactions:
- [Facebook Research's paper about extracting categorical features from trees](https://research.fb.com/publications/practical-lessons-from-predicting-clicks-on-ads-at-facebook/)
- [Example: Feature transformations with ensembles of trees (sklearn)](http://scikit-learn.org/stable/auto_examples/ensemble/plot_feature_transformation.html)
