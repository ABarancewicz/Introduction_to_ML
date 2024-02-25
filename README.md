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
  - [Setting up git](#set_git)
  - [Git in command line](#cl_git)
- [Learning Python](#python)
  - [Intro to python](#pyth_intro)
  - [Debugging python](#debugging)
  - [Virtual environments](#venv)
- [Data Extraction and Management](#data)
  - [Data files](#files)
- [Basic Theory](#basic)
  - [Calculus](#calc)
  - [Linear Algebra](#algebra)
- [Phylogenetics](#phylo)
- [Sequence Space Visualisations](#seq_vis)
  - [Dimensionality reduction](dim_red)
  - [Principle component analysis](#pca)
  - [t-distributed stochastic neighbour embedding](#tsne)
  - [Uniform Manifold Approximation and Projection](#umap)
- [Machine Learning Introduction](#ml)
  - [What is machine learning](#what_ml)
  - [Regression and Classification](#reg_clas)
  - [Non-Deep vs Deep methods](non-deep_deep)
- [Traditional Machine Learning](#trad_ml)
  - [k-nearest neighbours](#knn)
  - [Support vector machine](#svm)
  - [Random forest](#rf)
- [Deep Learning](#deep)
  - [Neural networks](#nn)
  - [Transformers](#transformers)
- [Validation and selection of hyperparameters](#hyper)
- [Implementation of Machine Learning](#implement)
- [Hardware for Machine Learning](#hardware)
</details>



## About this guide <a name="about"></a>
This guide is made as an introduction to using modern machine learning tools in protein engineering applications. It consists of 
this readme.md which contains a brief summary of various aspects of ML as well as links to more in-depth resources, and various 
exercises to teach how to actually run experiments.
The exercises are:
1. Basic git and bash - working in github repositories and running/editing scripts
2. Debbuging python - using vscode debugger to analyse what scripts are doing
3. Fundamental ML - One-hot encoding protein data and analysing with basic regression methods
4. ESM and data extraction - Extracting relevant information from a csv file, encoding with ESM, and analysing with basic regression
5. Neural networks - Analysing a protein dataset with a basic neural network
6. Transformers - Training a transformer to encode proteins into vectors




## Linux <a name="linux"></a>

### What is linux? <a name="what_linux"></a>

Linux is an open-source operating system which is free, reliable, and has a lot of community support. It is less user-friendly than Windows or MacOS, although
is very powerful and customisable. The Jackson Lab uses Ubuntu as its preffered Linux distribution. For the work covered in this introduction, the most important
aspect of Ubuntu is bash, the command processor which allows you to interact with your computer and files directly through text. If you are using a windows computer,
you may want to consider [installing WSL](https://ubuntu.com/desktop/wsl), and if you're on mac you may want to [set bash as your default shell](https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/). 

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
more functionality. A comprehensive guide on using bash is beyond the scope of this introduction, although if you have never used it before, I recommend following [the software carpentry
Unix Shell tutorial](https://software-carpentry.org/lessons/). Otherwise, here is a list of some basic commands you should know \(Note that a directory is just a folder\):
- ls - list the files and directories in the current directory
- cd - change the directory
- mkdir - create a new directory
- python3 - run a python file
- --help - enter after a function to get details on how to use it
- sudo apt install - install a package


## Git <a name="git"></a>

### What is Git? <a name="what_git"></a>

### Github <a name="github"></a>

### Git in command line <a name="cl_git"></a>

### Setting up git <a name="set_git"></a>



## Learning Python <a name="python"></a>

### Intro to python <a name="pyth_intro"></a>

### Debugging python <a name="debugging"></a>

### Virtual environments <a name="venv"></a>


## Data Extraction and Management <a name="data"></a>

### Data files <a name="files"></a>



## Basic Theory <a name="basic"></a>


### Calculus <a name="calc"></a>


### Linear Algebra <a name="algebra"></a>



## Phylogenetics <a name="phylo"></a>



## Sequence Space Visualisations <a name="seq_vis"></a>

### Dimensionality reduction <a name="dim_red"></a>

### Principle component analysis <a name="pca"></a>

### t-distributed stochastic neighbour embedding <a name="tsne"></a>

### Uniform Manifold Approximation and Projection <a name="umap"></a>


## Machine Learning Introduction <a name="ml"></a>

### What is machine learning? <a name="what_ml"></a>

### Regression and Classification <a name="reg_clas"></a>

### Non-deep vs Deep <a name="non-deep_deep"></a>


## Traditional Machine Learning <a name="trad_ml"></a>

### k-nearest neighbours <a name="knn"></a>

### Support vector machine <a name="svm"></a>

### Random forest <a name="rf"></a>


## Deep Learning <a name="deep"></a>

### Neural Networks <a name="nn"></a>

### Transformers <a name="transformers"></a>


## Validation and selection of hyperparameters <a name="hyper"></a>


## Implementation of Machine Learning <a name="implement"></a>


## Hardware for Machine Learning <a name="hardware"></a>


