## Basic Git 
- Basic Git commands are essential for everyday version control tasks like initializing a repository, adding and committing changes, and collaborating with others. These cover the fundamentals of managing a simple project.
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
- Notes: From **August 13, 2021**, Github remove support for [password authentication](https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls). Please check [this repository](https://github.com/NU-iz-da-fam/setup-SSH-key-github-repos) if you want to create a ssh-key for you account.
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
- Verify the remote and kind of clone (ssh/https):
    ```
    git remote -v
    ```
### 4. Basic Git Workflow
- This basic git workflow is essential and very common for developer at all levels.
- Check the status of your repository. This will help display the current state of the working directory.
    ```
    git status
    ```
- Add files to staging. Assume that you stage 'filename'
    ```
    git add filename
    ```
- To add all modified files:
    ```
    git add .
    ```
- Commit changes with message:
    ```
    git commit -m"Your message"
    ```
- If you're working on existing git repository. Pull, then push your commit:
    ```
    git pull
    ```
    ```
    git push
    ```

- If your local branch is new, you need to push to the remote repository:
    ```
    git push -u origin local_branch_name 
    ```
### 5. Branching
- List all branches
    ```
    git branch -l
    ```
- Rename current branch
    ```
    git branch -m <new-branch-name>
    ```
- Create and switch to a new branch
    ```
    git checkout -b [branch-name]
    ```
- Compare branches
    ```
    git diff <branch-1> <branch-2>
    ```
- Switch to another branch
    ```
    git checkout [branch-name]
    ```
- Delete a branch
    - Safe delete: only delete if branch has been merged
    ```
    git brach -d [branch-name]
    ```
    - Force delete: if you want to delete this branch immediately.
    ```
    git brach -D [branch-name]
    ```
### 6. Merging
- Assume you're on branch ```dev```, you want to merge branch ```tmp``` to dev:
    ```
    git merge tmp
    ```
- Merge 2 branches that have different histories. This type of merge is dangerous, please ensure you understand how it work before merging
    ```
    git merge tmp --allow-unrelated-histories
    ```
    - Then solving conflicts and commit.
### 7. Commit history
- To show the commit history
    ```
    git log
    ```
