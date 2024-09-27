## Basic Git 

### 1. Install Git
- In linux, run below command in terminal:
    ```
    sudo apt-get install git
    ```
### 2. Configure Git
- Set your name and email, which will appear in your commits.
    ```
    git config --global user.name "Your Name"
    git config --global user.email "you@example.com"
    ```
- This name and email will appear when you push your code to repository.
### 3.1. Work with an existing repository
- When working with an existing repos, you only need to clone, then use with git workflow.
    ```
    git clone https://github.com/user/repo.git
    ```
### 3.2. Create and work on new repository
- Navigate to your project directory and initialize a new Git repository:
- Use below commands:
    ```
    cd /path/to/your/project
    git init
    ```
- Add local repos to the remote repos. If remote repos has not been created yet, pls create and copy URL.
    ```
    git remote add origin https://github.com/your-username/your-repo.git
    ```
- Now, push your existing local commits to the remote repository. If you're pushing the main branch:
    ```
    git push -u origin main
    ```
- Verify the remote:
    ```
    git remote -v
    ```
### 4. Basic Git Workflow
- Check the status of your repository. This will help display the current state of the working directory.
    ```
    git status
    ```
