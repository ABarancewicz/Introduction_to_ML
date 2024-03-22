# Exercise 3: Basic Machine Learning

## Summary
In this project we will be trying to model the nascent transcription rate of yeast genes based on the data from [this study.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2982843/). We will be doing this through very basic methods to get some understanding of the workflow of a machine learning project. We will not be attempting to optimise any aspects of this pipeline, including hyperparameters of models and architecures used. While working through it could be useful to think about what the problems are with this pipeline and what better alternatives may be.
/

The pipeline we will follow for this exercise is:
1. Retrieve relevant protein sequences from UniProt
2. One-hot encode protein sequences
3. Reduce dimensionality with PCA, TSNE, and TSVD and look for clustering
4. Train a knn model with a training subset of our data
5. Test how well our model works with the testing subset of our data


