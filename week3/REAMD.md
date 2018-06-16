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







