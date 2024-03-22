# Exercise 3: Basic Machine Learning

## Summary
In this project we will be trying to model the nascent transcription rate of yeast genes based on the data from [this study.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2982843/). We will be doing this through very basic methods to get some understanding of the workflow of a machine learning project. We will not be attempting to optimise any aspects of this pipeline, including hyperparameters of models and architecures used. While working through it could be useful to think about what the problems are with this pipeline and what better alternatives may be.

## How to use this exercise
In the E3 directory there is this readme.md which contains the general overview of the exercise, [this jupyter notebook](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3%20-%20Basic%20ML/E3_basic_ML.ipynb) which contains the completed code of this exercise \(essentially the answers\), [this csv](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3%20-%20Basic%20ML/yeast_gene_tr.csv) which is taken from the study we are looking at and contains our data, and [this fasta](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3%20-%20Basic%20ML/unprocessed.fasta) which contains the sequences I was able to get from UniProt \(more on this later\). It is recommended that you try to work through each section of this readme.md, only looking at [E3_basic_ML.ipynb](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3%20-%20Basic%20ML/E3_basic_ML.ipynb) if you get stuck. 

## Thinking about how to approach this ML task
The first step to getting started is to make it clear to ourselves what we aim to do. In this case the data we are analysing comes from a [csv file](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3%20-%20Basic%20ML/yeast_gene_tr.csv) from [this study.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2982843/), containing protein names and their transcription rate \(TR\) which is the variable we are interested in modelling. Since this file doesn't contain protein sequence, we need to come up with a way to retrieve the correct sequences for each protein. Once we have the sequences we need to vectorise them so that the can fed into machine learning algorithms. We can then have a look for any clustering of data and reduce complexity of our vectors with some dimensionality reduction techniques. Finally, we can train a model on our data and test if it works well.

To set it out clearly, we need to:
1. Retrieve sequences corresponding to proteins in our dataset
2. Vectorise these sequences
3. Reduce dimensionality
4. Train a model
5. Test our model

The way that we will do all this is:
1. Retrieve relevant protein sequences from UniProt
2. One-hot encode protein sequences
3. Reduce dimensionality with PCA, TSNE, and TSVD and look for clustering
4. Train a knn model with a training subset of our data
5. Test how well our model works with the testing subset of our data

Just to reemphasise, none of these steps are necessarily the best way of creating an accurate model, although they do demonstrate the general process that is required.

## Setting up a working environment for this exercise
It is recommended that you create a directory for this exercise \(or clone this repository and work in E3-Basic_ML\) and work in a.ipynb file so you can easily write and run your code in chunks. 



