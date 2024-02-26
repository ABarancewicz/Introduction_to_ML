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

Note that this introduction is not comprehensive and may contain errors. If something doesn't make sense research into it, ask for help, or use
chatgpt to explain /(with caution/). Furthermore, it is possible that not all of the information contained in here will be relevant to your project.

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
more functionality. Terminal is both a built-in app in Ubuntu, and can also be accessed through VScode. A comprehensive guide on using bash is beyond the scope of this introduction,
although if you have never used it before, I recommend following [the software carpentry Unix Shell tutorial](https://software-carpentry.org/lessons/). Otherwise, here is a list 
of some basic commands you should know \(Note that a directory is just a folder\):
- ls - list the files and directories in the current directory
- cd - change the directory
- mkdir - create a new directory
- python3 - run a python file
- --help - enter after a function to get details on how to use it
- sudo apt install - install a package

\
For more helpful commands view [this article](https://www.guru99.com/linux-commands-cheat-sheet.html).


## Git <a name="git"></a>

### What is Git? <a name="what_git"></a>

Git is a type of version control software which is used by developers to track changes to files and to jointly work on projects. It can be used through graphical interfaces and through
bash. Git utalises repositories, essentially a folder to store all the files and documents related to one project. Using git to edit a remote repository \(such as on github\) follows the process:
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
\
\
If you don't have a Github account, you should make one. You can use this to create a portfolio of coding for future employers to view. You can also join the Jackson lab github
repository.

### Git in command line <a name="cl_git"></a>

#### Setting up git <a name="set_git"></a>

The first step to accessing github via the command line is to [install git](https://docs.gitlab.com/ee/topics/git/how_to_install_git/index.html). Once git is installed you need to 
link your computer to your github account. You can do that by following the 'Configure Git' steps in [this Gitlab article](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html)
/(Gitlab is an alternative to Github, although uses the same steps). Next you need to [set up an SSH key and connect it to Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) so that your computer is authenticated when you try to access repositories. 

#### Using git <a name="use_git"></a>

[This article](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) explains how to clone repositories in command line and how to initialise a repository in an existing directory. 
[Exercise 1](https://github.com/ABarancewicz/Introduction_to_ML/tree/main/E1-bash_and_git) is an introduction to git and bash and explains how to
clone and edit repositories. 

## Python <a name="python"></a>

### Intro to python <a name="pyth_intro"></a>

Python is a high level language designed to be easy to use and powerful. It is the language of choice for many scientists for more general applications,
and a very popular language for machine learning. This is because it has a huge community which create packages /(libraries of code that you can import 
and use in your project/) which are highly optimised and can perform many tasks. These packages mean you rarely have to do much coding, instead utalising
functions and algorithms from these packages. 
\
\
There are many courses available to learn python, such as [Code Academy](https://www.codecademy.com/) and a [Software Carpentry tutorial](https://software-carpentry.org/lessons/).
[LeetCode](https://leetcode.com/problemset/) is a website with many programming problems and solutions, and can be used to both learn and practice.
This introduction assumes you are familiar with python, if you understand the following terms and how they work in python you should be ok to continue:

- Functions
- Classes
- Data types (strings, floats, integers, dictionaries, lists, tuples, sets)
- Indexing and slicing
- Methods
- if/for/while statements
- Importing and using libraries


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


