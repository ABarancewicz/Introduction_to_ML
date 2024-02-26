# Exercise 1: Using bash and git

## Summary
In this exercise you will:
1. Make a new repository in your Github account
2. Clone the repository
3. Learn how to navigate through directories in command line
4. Create and run a basic python script 

## Prerequisites
This exercise assumes you have read through the [main readme.md](https://github.com/ABarancewicz/Introduction_to_ML/blob/main/README.md) up to 
and including the section on git. Make sure you have installed git, set your username and email, and created SSH keys and added them to your account.

## Step 1: Creating the repo
Login to [Github](https://github.com) and navigate to your repositories page and create a new repository called "ML_Intro_E1". Note that you can 
set the repo to be publically available on your account or visible only to you.

## Step 2: Navigate to your working directory
Now we need to choose where we want to clone the repo to. Open up the terminal app or a bash terminal in VS code. The default directory is called your 
home directory, while the directory that bash is currently in is called the working directory. To start we should look at where our current working 
directory is by typing.

```
pwd
```
To view everything that is in that directory type:

```
ls
```
To change the working directory use the cd command. For example if you wanted to move into the Documents directory, you would type:
```
cd Documents
```
Remember that you can use tab completion, type out part of what directory you want to move into and then press tab to autocomplete. 
You can also chain paths together with '/' (eg Documents/Homework) and can move back a directory with 'cd ..'

## Step 3: Cloning the repo
To clone your repo type:
```
git clone git@github.com:USERNAME/ML_Intro_E1.git
```
You will likely get a warning saying that you cloned an empty repository.

## Step 4: Editing the repo
Now that you have a local version of the repository on your computer. You can make new files and folders in here and edit files just as you would 
any other folder on your computer. We will make a basic python script to print a message. To do this create a new python file in VS code with the
following code
```
print("This is the output")
```
Save the file in the ML_Intro_E1 directory as ML_print.py.

## Step 5: Running ML_print.py via command line
To run ML_print.py through command line make sure you have ML_Intro_E1 as your working directory. If you type 'ls' you should see ML_print.py,
which you can run in bash by typing:
```
python3 ML_print.py
```
You should get "This is the output" printed onto your terminal.
## Step 6: Add, commit, and push
Finally we can send these changes to the Github repository by typing:
```
git add -A
git commit -a -m "created ML_print.py"
git push
```
Remember to use -help after a command to understand what it does and what options are available. Eg:
```
git commit -help
```

## Step 7: Checking the remote repo
Now you can log into github.com and confirm that the changes have been added into your repository.


