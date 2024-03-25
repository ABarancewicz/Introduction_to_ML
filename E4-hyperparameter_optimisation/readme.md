# Exercise 4: Hyperparameter optimisation

## Summary
We will be using a deep mutations scan dataset of PTEN from [this paper](https://www.nature.com/articles/s41588-018-0122-z) and will try to model the protein abundance with one-hot encoding and basic regression methods. In this exercise, we will also try to implement hyperparameter optimisation to improve our model. Unlike in E3, this dataset contains highly related proteins (each protein is the same expect for a point mutation), which means our one-hot encoding should work much better. 

## How to use this exercise
As with E3, it is suggested you follow along this readme.md and try to finish each step yourself. It is a jupyter notebook and a venv made for this project. We are using the PTEN dataset from [this database](https://abundance.gs.washington.edu/shiny/stability/), which can be downloaded although is also saved here as [PTEN.csv](https://github.com/ABarancewicz/Introduction_to_ML/edit/main/E4-hyperparameter_optimisation/PTEN.csv)

## Thinking about how to approach this ML task

