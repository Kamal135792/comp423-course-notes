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

    !!! question "What does this command do???"

        "This command creates a connection, or "tracking relationship," between your local feature-awesome branch and a new branch of the same name on the remote repository. This tracking relationship is important – once established, it lets you use simple git push and git pull commands without having to specify the remote and branch names each time." - Kris Jordan

Now we have a project that uses git for version control and GitHub to host our code remotely. Let's move to the next portion where we will setup our Dev Container.

## Step 2: Setting up the Dev Container ##

### Add Development Container Configuration ###

1. Run Docker
3. In VS Code, open your projects folder. You can do this via: File > Open Folder.
4. Install the Dev Containers extension for VS Code.
5. Create a ``.devcontainer`` directory in the root of your project
6. Inside the ``.devcontainer`` directory add this file ``devcontainer.json``
7. Inside the devcontainer.json file add the following code:

    ```json
    {
    "name": "go project",
    "image": "mcr.microsoft.com/devcontainers/go:latest",
    "customizations": {
            "vscode": {
            "settings": {},
            "extensions": ["golang.Go"]
            }
        }
    }
    ```

    In this code we are specifying the following:
    
    - ``name``: A descriptive name for your dev container.
    - ``image``: The Docker image to use, in this case, the latest version of a Python environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!
    - ``customizations``: Adds useful configurations to VS Code, like installing extensions. By adding extensions here we can ensure other developers on your project have them installed in their dev containers automatically.

8. Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed. 
    
    !!! warning "If you are experiencing errors"
        Make sure you have Docker running, make sure you saved your ``devcontainer.json`` file, try to close and reopen VS Code and Docker.

9. Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running ``go version`` to see your dev container is running a recent version of Go.

## Writing a Hello World Program ##

### Creating the file ###

1. Inside your projects directory create a file called ``main.go``.
2. Copy this boilerplate code into the file:

    ```Go
    package main

    import "fmt"

    func main() {
        
    }
    ```

3. Write the code to print "Hello COMP423!" by putting this into your ``main`` function:

    ```Go
    fmt.Println("Hello COMP423!")
    ```

### Building and Running the Program ###

1. We can create a Go module to make sure to track our dependancies using this command:

    ``go mod init <name>``

    !!! question "What this does"
        The command creates a ``go.mod`` file which will manage our dependancies and versions in our Go project. Similar to the purpose of the Dev Container, this makes it easier for a team to collaborate because everyone can use the same dependancies and versions of these dependancies.

2. Now finally we can run our program by using this command:

    ``go run main.go``

    If done correctly, it should output "Hello World!".

3. To build the program into a binary file run the following command:

    ``go build -o hello-world main.go``

    If done correctly, it should create an executable file called ``hello-world``.
    
3. Now we can run the executable file we just created using the following command:

    ``./hello-world``

    If done correctly, it should output "Hello World!".

!!! question "What's the difference between the `run` and `build` commands"
    Go is a compiled language. This means that a compiler turns the code we write into executable code before running it. So whats actually happening when we use `go run` is that is that the code is compiled into a temporary file then executed, which makes this command useful for quick testing or debugging errors. However, when we use `go build` we are creating the actual executable file that can be run without a Go environment. This is similar to the `gcc` command that is used in the C programming language which creates a executable file that you can later run. This method is useful for when you have a completed product that you are ready to distribute or deploy.


Congratulations, now you have created your first program in Go! Good luck on your programming journey!
















    







