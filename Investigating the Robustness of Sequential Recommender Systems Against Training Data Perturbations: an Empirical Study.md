
# Investigating the Robustness of Sequential Recommender Systems Against Training Data Perturbations: An Empirical Study

### Links:

[PDF](https://arxiv.org/pdf/2307.13165.pdf)

Implementation code: The authors used RecBole, but did not provide code.

### Idea:

We can remove some elements from sequences and see how this affects performance. Removing elements from the beginning, middle and end can be done in practice.

### Method:

The authors took SASRec and GRU4Rec, they removed different numbers of elements in the training sequences in three ways: from the beginning, middle and end. They study performance and ranking degradation.

### Experiments:

![Image](https://github.com/fotol1/RecSysPapersReviews/blob/master/images/exp1.png)

Removing elements from the beginning and middle does not affect performance. Removing elements from the end greatly reduces the quality of the recommendations.

### Strength:

* The scenario considered may occur in practice. For example, offline recommender systems update predictions with some time intervals. Users generate new interactions, but the model does not have time to take them into account. This is "removing from the end".
* The experiments show valuable results for different metrics and hyperparameters (e.g. number of elements removed).

### Weakness:

* The authors do not consider models that can be robust to such changes in the training data. They mention some methods in related work, but do not include them in the experiments.
* General recommenders could potentially correct the degradation because they do not know the order of the interactions. Unfortunately, the comparison between sequential and non-sequential models is not provided.

### Random thoughts:

* The degradation of quality with missing last elements of interactions seems appropriate for sequential recommendations. When predictions are heavily based on recent interactions, they affect performance heavily. If authors remove final elements, the remaining elements force next-item models to predict the removed items. If the model is robust to such interventions in training data, is it still a next-item recommender?
