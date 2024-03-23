# Exercise 3: Basic Machine Learning

## Summary
In this project we will be trying to model the nascent transcription rate of yeast genes based on the data from [this study.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2982843/). We will be doing this through very basic methods to get some understanding of the workflow of a machine learning project. We will not be attempting to optimise any aspects of this pipeline, including hyperparameters of models and architecures used. While working through it could be useful to think about what the problems are with this pipeline and what better alternatives may be.

## How to use this exercise
In the E3 directory there is this readme.md which contains the general overview of the exercise, [this jupyter notebook](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/E3_basic_ML.ipynb) which contains the completed code of this exercise \(essentially the answers\), [this csv](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/yeast_gene_tr.csv) which is taken from the study we are looking at and contains our data, and [this fasta](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/unprocessed.fasta) which contains the sequences I was able to get from UniProt \(more on this later\). It is recommended that you try to work through each section of this readme.md, only looking at [E3_basic_ML.ipynb](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/E3_basic_ML.ipynb) if you get stuck. 

## Thinking about how to approach this ML task
The first step to getting started is to make it clear to ourselves what we aim to do. In this case the data we are analysing comes from a [csv file](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/yeast_gene_tr.csv) from [this study.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2982843/), containing protein names and their transcription rate \(TR\) which is the variable we are interested in modelling. Since this file doesn't contain protein sequence, we need to come up with a way to retrieve the correct sequences for each protein. Once we have the sequences we need to vectorise them so that the can fed into machine learning algorithms. We can then have a look for any clustering of data and reduce complexity of our vectors with some dimensionality reduction techniques. Finally, we can train a model on our data and test if it works well.

To set it out clearly, we need to:
1. Retrieve sequences corresponding to proteins in our dataset
2. Vectorise these sequences
3. Split our data into testing and training subsets
4. Reduce dimensionality
5. Train a model
6. Test our model

The way that we will do all this is:
1. Retrieve relevant protein sequences from UniProt
2. One-hot encode protein sequences
3. Split our data into testing and training subsets
4. Reduce dimensionality with PCA, TSNE, and TSVD and look for clustering
5. Train a knn model with a training subset of our data
6. Test how well our model works with the testing subset of our data

Just to reemphasise, none of these steps are necessarily the best way of creating an accurate model, although they do demonstrate the general process that is required.

## Setting up a working environment for this exercise
It is recommended that you create a directory for this exercise \(or clone this repository and work in this directory\) and work in a.ipynb file so you can easily write and run your code in chunks. You also should work with a python virtual environment created for this introduction to ML.

## Step 1: Retrieving sequences from UniProt
The first step is to retrieve sequences corresponding to our proteins. See if you can retrieve all sequences with a gene name corresponding to the 'sistematic name' or 'gene name' columns in our [data csv file](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/yeast_gene_tr.csv) from the [UniProt ID mapping tool](https://www.uniprot.org/id-mapping). Note that some proteins may be listed under both the systematic name and gene name, resulting in multiple of the same sequence being retrieved, we will fix this later. The output of the UniProt ID mapping tool should be able to be downloaded as a FASTA file. If you cannot get this to work you can continue this exercise with [unprocessed.fasta](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/unprocessed.fasta)

## Step 2: Formatting our FASTA file to include transcription rates and contain no duplicates
The next step is to neatly organise our data. This means we need to remove any duplicates from the FASTA file we just retrieved, and make the headers of each sequence more informative. We will be using the 'TR \(mol/min\) dilution corrected' as the target variable that we are trying to model, which we will call tr. A good format for a FASTA file here is something like this:
```
>gene_name|tr
protein_sequence
>gene_name|tr
protein_sequence
```
Try to use google and ChatGPT to generate such a FASTA file called 'processed.fasta'. If you get stuck you can refer to [E3-basic_ml.ipynb](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/E3-basic_ml/E3_basic_ML.ipynb).

## Step 3: One-hot encoding the protein sequences
From processed.fasta we now want to get a list of one-hot encoded protein sequences and a corresponding list of tr values. To one-hot encode our sequences we will use [scikit_learn's OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html) as it has much more functionality than any script that we or ChatGPT would write. Take note of what input OneHotEncoder expects and try to parse through processed.fasta and generate a sequences variable in the correct format, and a tr variable with the corresponding tr values. 

A result of one-hot encoding our protein sequences is greatly increasing the number of dimensions, as each position gets seperated into a feature for each amino acid found at that position. When I ran this one_hot_sequences ended up being a matrix with 1306 rows and 40539 columns \(you can check yours with one_hot_sequences.shape\). Another result is that our data is very sparse, meaning most features are 0.

## Step 4: Splitting data into testing and training datasets
Now that we have our vectorised data we need to split it into testing and training subsets. To do this we will use [scikit_learn's train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html) function. 

## Step 5: Dimensionality reduction
Dimensionality reduction is a standard way to reduce the size of data while maintaining salient features of the data. This is done to visually show clustering of data and to reduce the amount of data being fed into algorithms, which speeds up computation. Using scikit_learn we will try [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html), [TSVD](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.TruncatedSVD.html), and [TSME](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) on our training datasets.

Since our data is very sparse, these dimensionality reduction techniques don't work very well to visualise patterns in the data. It is, however, a good example of how differently these methods transform data. Compare the shapes of the graphs of components 1 and 2 of each technique. 

## Step 6: Testing and training a k-nearest neighbours model
Now that we have reduced the dimensionality of our data, we can train our knn model. We will be using [scikit learn's knn regressor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html). You can try training on any or all of the dimensionality reduced training sets, and testing the model's accuracy against the testing dataset \(processed with the same dimensionality reduction model\). 

## Step 7: Improving this experiment
Think about the ways that we could improve this experiment. How could we optimise our knn hyperparameters? What vectorisation methods may give us more informative data? What other regressor architectures could yield better results?
