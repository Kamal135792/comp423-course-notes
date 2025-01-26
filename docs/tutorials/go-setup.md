# Setting up a dev container for Go

* Primary author: [Kamal Deep Vasireddy](https://github.com/Kamal135792)
* Reviewer: [Kaw Bu](https://github.com/kawbu)

## Prerequisites ##

These are the prerequisites you are expected to have before starting this tutorial. 
Make sure you have these before starting the tutorial.

1. Visual Studio Code - This will be the primary code editor. Download it [here](https://code.visualstudio.com/download)
2. Github account - This will be where we host our project for others to see and collaborate with. Signup [here](https://github.com/signup)
3. Git installed - This will be our primary version control system. Download it [here](https://git-scm.com/downloads)
4. Docker installed - This will be used for our dev container. Download it [here](https://www.docker.com/get-started/)


## Step 1: Creating a New Directory, Git Initialization, and Connecting to GitHub ##

### Creating a Directory ###

To start you will create a directory where you will store your project files. 

1. Open your terminal or command prompt.
2. Run the following command to create a new directory.

    ```bash
    mkdir go-project
    ```

This will create a new folder called ``go-project`` in your current directory.

### Navigating to the Directory ###

After you create this directory navigate to it using this command.
``` bash
cd go-project
```
This will make ``go-project`` your current working directory.

### Git Initialization ###

Now that we are in the proper directory, lets initialize git to handle version control.

1. use the following command to initialize a Git repo.
    
    ```bash
    git init
    ```

2. To make sure that this command worked run

    ```bash
    git status
    ```

    This should output that you are on the main or master branch and that you have no commits yet.

### Connecting to GitHub ###

Now that we have a git repo, lets create a remote repository on GitHub that will store our code. To do this follow these steps.

1. Go to your GitHub account [GitHub](https://github.com/)
2. On the top right click the  "+" sign and click "New repository"
3. Create the repo using these details:
    - Name: go-project
    - Description (optional): My first Go project.
    - Your preference for public or private
    - Do not initialize the repo with a README, .gitignore, or license.
4. Lets create a README file to commit. Run these commands:
    
    ```bash
    echo "# go-project" >> README.md
    git add README.md
    git commit -m "first commit"
    ```

5. Check what your branch name is by using this command:
    
    ```bash
    git branch
    ```

    If is it "master" lets rename it to "main" by using this command.

    ```bash
    git branch -M main
    ```

6. Now let's add your GitHub repo as your remote origin by running this command:

    ```bash
    git remote add origin https://github.com/<your-github-username>/go-project.git
    ```

7. Now let's push your local changes to GitHub. Run this command:

    ```bash
    git push --set-upstream origin main
    ```

    !!! info "What does this command do???"

        "This command creates a connection, or "tracking relationship," between your local feature-awesome branch and a new branch of the same name on the remote repository. This tracking relationship is important – once established, it lets you use simple git push and git pull commands without having to specify the remote and branch names each time." - Kris Jordan

Now we have a project that uses git for version control and GitHub to host our code remotely. Let's move to the next portion where we will setup our Dev Container.

## Step 2: Setting up the Dev Container ##

### Add Development Container Configuration ###

1. In VS Code, open your projects folder. You can do this via: File > Open Folder.
2. Install the Dev Containers extension for VS Code.
3. Create a ``.devcontainer`` directory in the root of your project
4. Inside the ``.devcontainer`` directory add this file ``devcontainer.json``










    







