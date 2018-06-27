# Agenda
## Problem formulation
CrowdFlower: relevant searching
- a search query and some information about an item
1. query
2. product_title
3. product_description
4. median_relevance
5. relevance_variance

## Data
## Metric
- quadratic weighted kappa
- typical value range: [0 (random), 1(complete agreement)]
- may go below 0
In order to understand this metric, let's see how to calculate it.
### Text features:
- we have 3 text fields - a query, a title and a description
- That is, for (query, title) and (query, description) pairs
we calculated:
1. the number of matching words
2. Cosine distance between TF-IDF representations
3. Distance between the average word2vec vectors
4. Levenshtein distance
## 3 important points about data
- Queries are very short.
- Number of unique queries is 261
- Queries are the same in train and test.
### Sample weightining
- we are given variance of scores for each pair
- large variance means low confidence about label.
1. simple heuristic:
2. Restore indivudla scores using median and variance statistics:

### Kappa optimization
1. Metric has properties of both classification and regression
2. we consider task as regression
3. needed a way to turn real-valued predictions into classes
4. We varied thresholds for every class and select the best ones.
This significantly increased our score.

### Conclusion
1. Most importantn points of our solution.
2. symbolic n-grams
3. expansion of queries
4. optimization of thresholds for Kappa


## Advanced features and tricks
