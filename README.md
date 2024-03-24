# An introduction to Machine Learning for Directed Evolution
## By Anthony Barancewicz

<details open><summary><b>Table of contents</b></summary>
  
- [About this Guide](#about)
- [Linux](#linux)
  - [What is Linux](#what_linux)
  - [Installing linux](#install_linux)
  - [IDE](#ide)
  - [Terminal](#terminal)
- [Git](#git)
  - [What is git?](#what_git)
  - [Github](#github)
  - [Git in command line](#cl_git)
    - [Setting up git](#set_git)
    - [Using git](#use_git)
- [Python](#python)
  - [Intro to python](#pyth_intro)
  - [Debugging python](#debugging)
  - [Virtual environments](#venv)
- [Data Extraction and Management](#data)
  - [Data files](#files)
- [Basic Theory](#basic)
  - [Calculus](#calc)
  - [Linear Algebra](#algebra)
  - [Dimensionality reduction](#dim_red)
- [Phylogenetics](#phylo)
- [Sequence Space Visualisations](#seq_vis)
  - [Principle component analysis](#pca)
  - [t-distributed stochastic neighbour embedding](#tsne)
  - [Uniform Manifold Approximation and Projection](#umap)
- [Machine Learning Introduction](#ml)
  - [What is machine learning](#what_ml)
  - [Regression and Classification](#reg_clas)
  - [Non-Deep vs Deep methods](non-deep_deep)
- [Vector representations](#)
  - [One-hot encoding](#one-hot)
  - [Biophys properties?](#)
  - [ESM](#)
- [Traditional Machine Learning](#trad_ml)
  - [k-nearest neighbours](#knn)
  - [Support vector machine](#svm)
  - [Random forest](#rf)
  - [Gaussian process](#gaussian)
- [Deep Learning](#deep)
  - [Backprop](#)
  - [Multilayer Perceptrons](#nn)
  - [Recurrent neural networks](#)
  - [Transformers](#transformers)
- [Validation and selection of hyperparameters](#hyper)
- [Implementation of Machine Learning](#implement)
  - [Scikit Learn](#)
  - [Pytorch](#)
  - [Pytorch lightning](#)
  - [Hugging face](#)
- [Hardware for Machine Learning](#hardware)
</details>



## About this guide <a name="about"></a>
This guide is made as an introduction to using modern machine learning tools in protein engineering applications. It consists of 
this readme.md which contains a brief summary of various aspects of ML as well as links to more in-depth resources, and various 
exercises to teach how to actually run experiments.
The exercises are:

1. [Basic git and bash](https://github.com/ABarancewicz/Introduction_to_ML/tree/main/E1-bash_and_git) - working in github repositories and running/editing scripts
2. Debbuging python - using vscode debugger to analyse what scripts are doing
3. [Fundamental ML](https://github.com/ABarancewicz/Introduction_to_ML/tree/main/E3-basic_ml) - one-hot encoding protein data and analysing with basic regression methods
4. Hyperparameter tuning - using GridSearch CV and RandomSearch CV to optimise hyperparameters
5. ESM and data extraction - extracting relevant information from a csv file, encoding with ESM, and analysing with basic regression
6. Neural networks - analysing a protein dataset with a basic neural network
7. Transformers - training a transformer to encode proteins into vectors

Note that this introduction is not comprehensive and may contain errors. If something doesn't make sense research into it, ask for help, or use
chatgpt to explain (with caution). Furthermore, it is possible that not all of the information contained in here will be relevant to your project.

## Linux <a name="linux"></a>

### What is linux? <a name="what_linux"></a>

Linux is an open-source operating system which is free, reliable, and has a lot of community support. It is less user-friendly than Windows or MacOS, although
is very powerful and customisable. The Jackson Lab uses Ubuntu as its preffered Linux distribution. For the work covered in this introduction, the most important
aspect of Ubuntu is bash, the command processor which allows you to interact with your computer and files directly through text. If you are using a windows computer,
you may want to consider [installing WSL](https://ubuntu.com/desktop/wsl), and if you're on mac you may want to [set bash as your default shell](https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/). 
Note: it is likely that everything we do could be done on windows, although you would need to research how to do so as terminal syntax will be different.

### Installing Linux <a name="install_linux"></a>

If you choose to install linux onto your computer you can do so by following [Ubuntu's install instructions](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview), 
or if you need both linux and another operating system on your computer you can look into [dual booting](https://answers.syr.edu/display/ITHELP/Dual+Booting), although 
make sure that you look into the risks associated with dual booting and make a full system backup in case something goes wrong. 

### IDE <a name="ide"></a>

While scripts are typically just text files and can be created and edited through a basic text editor, programmers typically install an integrated development environment \(IDE\)
to make coding easier. IDEs typically offer features such as syntax highlighting to make code more legible, and other tools such as debugging tools and more recently integration of
ChatGPT-like software to help with coding. The IDE preffered by the Jackson lab is [Visual Studio Code](https://code.visualstudio.com/) and can be installed in the Ubuntu software app. 

### Terminal <a name="terminal"></a>

Terminal, also known as command line, is how one can directly interact with files and your computer through bash. You can think of it as a text-based version of file manager with
more functionality. Terminal is both a built-in app in Ubuntu, and can also be accessed through VScode. A comprehensive guide on using bash is beyond the scope of this introduction,
although if you have never used it before, I recommend following [the software carpentry Unix Shell tutorial](https://software-carpentry.org/lessons/). Otherwise, here is a list 
of some basic commands you should know \(Note that a directory is just a folder\):
- ls - list the files and directories in the current directory
- cd - change the directory
- mkdir - create a new directory
- python3 - run a python file
- --help - enter after a function to get details on how to use it
- sudo apt install - install a package

For more helpful commands view [this article](https://www.guru99.com/linux-commands-cheat-sheet.html).


## Git <a name="git"></a>

### What is Git? <a name="what_git"></a>

Git is a type of version control software which is used by developers to track changes to files and to jointly work on projects. It can be used through graphical interfaces and through
bash. Git utilises repositories, essentially a folder to store all the files and documents related to one project. Using git to edit a remote repository \(such as on github\) follows the process:
1. Clone - this copies the chosen remote repository to your computer. In practice this repository just becomes a folder full of all the files on the repository.
2. Make changes to your local version of the repository
3. Commit - this updates your local version of the repository with the changes you made
4. Push - this updates the remote repository with the committed changes.

Other terms used in git are:
 - Fetch - This updates your local repository to match the remote repository
 - Pull - This updates your workspace to match the remote repository

For more information you can follow the [version control with git software carpentry tutorial](https://software-carpentry.org/lessons/) and read [this article](https://medium.com/@mehulgala77/github-fundamentals-clone-fetch-push-pull-fork-16d79bb16b79).

### Github <a name="github"></a>

Github is a website that offers cloud-based hosting for git repositories, allowing repositories to easily be shared both publicly and privately. It can be interacted through 
a GUI via the [github website](https://github.com/) or [github desktop](https://desktop.github.com/). In this introduction, however, we will be interacting with Github through 
command line.

If you don't have a Github account, you should make one. You can use this to create a portfolio of coding for future employers to view. You can also join the Jackson lab github
repository.

### Git in command line <a name="cl_git"></a>

#### Setting up git <a name="set_git"></a>

The first step to accessing github via the command line is to [install git](https://docs.gitlab.com/ee/topics/git/how_to_install_git/index.html). Once git is installed you need to 
link your computer to your github account. You can do that by following the 'Configure Git' steps in [this Gitlab article](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html)
(Gitlab is an alternative to Github, although uses the same steps). Next you need to [set up an SSH key and connect it to Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) so that your computer is authenticated when you try to access repositories. 

#### Using git <a name="use_git"></a>

[This article](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) explains how to clone repositories in command line and how to initialise a repository in an existing directory. 
[Exercise 1](https://github.com/ABarancewicz/Introduction_to_ML/tree/main/E1-bash_and_git) is an introduction to git and bash and explains how to
clone and edit repositories. 

## Python <a name="python"></a>

### Intro to python <a name="pyth_intro"></a>

Python is a high level language designed to be easy to use and powerful. It is the language of choice for many scientists for more general applications,
and a very popular language for machine learning. This is because it has a huge community which create packages (libraries of code that you can import 
and use in your project) which are highly optimised and can perform many tasks. These packages mean you rarely have to do much coding, instead utilising
functions and algorithms from these packages. 

There are many courses available to learn python, such as [Code Academy](https://www.codecademy.com/) and a [Software Carpentry tutorial](https://software-carpentry.org/lessons/).
[LeetCode](https://leetcode.com/problemset/) is a website with many programming problems and solutions, and can be used to both learn and practice.
This introduction assumes you are familiar with python, if you understand the following terms and how they work in python you should be ok to continue:

- Functions (using and defining)
- Classes
- Data types (strings, floats, integers, dictionaries, lists, tuples, sets)
- Indexing and slicing
- Methods
- if/for/while statements
- Importing and using libraries


### Understanding and debugging python <a name="debugging"></a>
When you code in python you will inevitably run into errors or not understand what your code is doing. The key to debugging code is to understand it, and regardless of 
whether your code is working or not it is always good to understand how it works. 

The first thing to do is make sure you understand the functions that you use in their code. All functions that you use that are from base python or any popular libraries will
have good documentation explaining what functions expect as inputs, what they provide as outputs, and the various parameters of the function. Take a look at [the numpy log function](https://numpy.org/doc/stable/reference/generated/numpy.log.html)
to familiarise yourself with documentation. What data types are expected in input? What does the function do? What is the datatype of the output? 

Another good idea is to look at how your data flows through your code. You can do this by using print() statements to look at different variables at different stages of code, 
or you can use the debugging mode in VScode to step through line by line and/or at specified break points and look at how variables change. 

If all else fails, google and ChatGPT often have the solutions to your problems. Google will often give links to articles or Stack Overflow threads that are written by real people, 
often experienced programmers. This means that often these solutions are correct, although may need some work to fit into your code. ChatGPT can provide tailored feedback on your code,
although is also prone to making things up. It can be very useful, as the amount of code and literature it has been trained on it enormous, but it is important to remember it has no 
actual understanding of what it says (especially for complicated or uncommon code). It can also be great for writing code and finding functions and can save you a lot of time, although
make sure you don't blindly trust what it gives you. To get the most out of ChatGPT I suggest that you be specific about:
- What language you are coding in
- What datatypes your variables are
- What your variables and files are called
- What exactly you are trying to do

### Virtual environments <a name="venv"></a>
Virtual environments are considered to be best practice when working with Python, but what are they? A virtual environment is essentially a place where 
you can install python packages without them being installed system-wide. By default, whenever you install a package into python it is installed into a 
folder in your base python installation. This means that when you install a package it will be present in all your python projects. This can make your python
gloval environment cluttered and can lead to reproducibility issues due to having many packages installed and not knowing which packages are required. 

Instead, good practice is to make a virtual environment for every project you work on. This means that you can install only the packages that are needed for 
your project, and others can easily reproduce your virtual environment so that they can run your code. The way that these environments are created is with the 
[venv command](https://docs.python.org/3/library/venv.html), and packages can be installed with [pip install](https://packaging.python.org/en/latest/tutorials/installing-packages/).

For a guide on how to use venv you can look at [this article](https://realpython.com/python-virtual-environments-a-primer/) or the [python documentation](https://docs.python.org/3/library/venv.html).
It is recommended that you make a virtual environment to use for all of the exercises in this guide.

### Packages

#### pandas

#### numpy

#### scipy

#### pytorch

#### Scikit_learn



## Data Extraction and Management <a name="data"></a>

### Data files <a name="files"></a>



## Basic Theory <a name="basic"></a>


### Calculus <a name="calc"></a>

### Linear Algebra <a name="algebra"></a>

### Dimensionality Reduction <a name="dim_red"></a>
Note: dimensionality reduction methods should be fit to the training dataset without the testing dataset. If they are fit to the total dataset it is a form of [data leakage](https://datascientest.com/en/data-leakage-definition-and-prevention) and means validation with your testing dataset may not accurately reflect your models accuracy.

## Phylogenetics <a name="phylo"></a>



## Sequence Space Visualisations <a name="seq_vis"></a>

### Principle component analysis <a name="pca"></a>

### t-distributed stochastic neighbour embedding <a name="tsne"></a>

### Uniform Manifold Approximation and Projection <a name="umap"></a>

[This explanation](https://umap-learn.readthedocs.io/en/latest/how_umap_works.html) is good.


## Machine Learning Introduction <a name="ml"></a>

### What is machine learning? <a name="what_ml"></a>

Machine learning (ML) is the term used to describe the training of a mode, based on provided data. The training and use of a machine learning model may typically look like:
1. Data selection and preparation. Appropriate data is chosen and processed in a way that can be fed into an algorithm.
2. Algorithm selection. Based on the chosen aim and dataset an appropriate algorithm must be chosen. Some commonly used types of algorythms are listed in the [non-deep]() and [deep]() ML sections of this guide. 
3.  Model training. The prepared data is split into a training set and validation set. The model's parameters are optimised to the training set. The validation set is used to verify that improvement in model performance is due to learning meaningful patterns in the data, and not just 'memorising' the training dataset.
4.  Using the model. Once the model is trained it can be applied to any collected or simulated data. 


### Regression and Classification <a name="reg_clas"></a>



### Non-deep vs Deep <a name="non-deep_deep"></a>

### Supervised vs Non-supervised <a name="sup_nonsup"></a>


## Traditional Machine Learning <a name="trad_ml"></a>

### k-nearest neighbours <a name="knn"></a>

k-nearest neighbours is one of the simplest methods of ML-based classification and regression. It works by calculating the distance between the query point and points in the training data set. It then calculates the target variable as the average of the closest k datapoints, weighted based on how close they are to the query point. 

[This IBM article](https://www.ibm.com/topics/knn) provides a great explanation of knn. 

### Support vector machine <a name="svm"></a>

### Random forest <a name="rf"></a>

### Gaussian Process <a name="gaussian"></a>


[Covariance matrix explained](https://www.youtube.com/watch?v=152tSYtiQbw)

[Basic gaussian process](https://towardsdatascience.com/an-intuitive-guide-to-gaussian-processes-ec2f0b45c71d)

[Gaussian process explained](https://distill.pub/2019/visual-exploration-gaussian-processes/#Multivariate)

## Deep Learning <a name="deep"></a>

### Neural Networks <a name="nn"></a>

### Transformers <a name="transformers"></a>


## Validation and selection of hyperparameters <a name="hyper"></a>


## Implementation of Machine Learning <a name="implement"></a>


## Hardware for Machine Learning <a name="hardware"></a>


