## Advanced Git
- Advanced Git refers to the more complex features and tools in Git that are used to handle tricky situations or optimize workflows in larger, more complex projects. 
- Advanced Git helps us manage history, resolve conflicts, and keep our project organized when things get complicated.

### 1. Git rebase
- Applies your changes on top of another branch's history. Unlike merging, it replays your commits on top of the target branch's latest state, producing a linear history.
    #### a. Standard Rebase:
    - ```git rebase specified-branch```: Rebases your current branch on top of the specified branch.
    - Example: Below command takes your ```feature-branch``` and replays all of its commits on top of the ```main``` branch.
        ```
        git checkout feature-branch
        git rebase main
        ```
    #### b. Interactive Rebase:
    - Allows you to modify your commit history (e.g., reordering commits, squashing multiple commits into one, editing commit messages).
    - Example: Below command opens an editor where you can interactively choose what to do with **the last 3 commits**.
        ```
        git rebase -i HEAD~3
        ```
**Detailed Rebase Process**
- Let’s say you have the following situation:
    ```
    main
    |
    A---B---C        (main)
        |
        D---E---F  (feature-branch)
    ```
- Now, you want to move **feature-branch** to be on top of the latest **main** branch (after commit C). 

**Before rebase**:
- The commits D, E, and F in feature-branch are based on an older version of main (commit B).

**After rebase**
- By running below commands:
    ```
    git checkout feature-branch
    git rebase main
    ```
- Git will apply the changes made in D, E, and F to the latest commit on main (commit C), effectively replaying those changes on top of it.
    ```
    main
    |
    A---B---C    (main)
            |
            D'---E'---F'  (feature-branch)
    ```
- Here, D', E', and F' are new commits that represent the same changes as D, E, and F, but rebased on top of commit C.

#### Difference between Git rebase and Git merge
**Merge**: When you merge, Git combines the two branches into one but keeps the history of both, which can result in a "merge commit" and a more complex history:
```
A---B---C---M
    \     /
    D---E---F
```
- Pros of Merge: 
    + Preserve complete history or avoid rewriting history.
    + Merge commit can sometimes cause look messy, but display clearly the evolution of features.

**Rebase**: Rebasing, on the other hand, avoids creating merge commits by rewriting history so that your commits appear as if they were made after the latest changes:
```
A---B---C---D'---E'---F'
```
- Pros of Rebase: 
    + Cleaner, linear history
    + Avoid unnecessary commits

- Image below describes in detail the difference between Git merge and git rebase. 

![alt text](images/merge_vs_rebase.png "comparison")

### 2. Git cherry-pick
### 3. Git stash
- Git stash is a git feature which temporarily saves uncommitted changes so you can work on something else without committing or losing your current work.

- Why using ```git stash```:
    + Save changes locally without dummy commit when suddenly switching to other task.
    + When done with ad-hoc task, you can go back and apply changes.
- Common ```git stash``` commands:
    + ```git stash``` / ```git stash save```: Saves your uncommitted changes. Assume you add file_1.txt
        ```
        git stash save 'Add file 1'
        ```
        Example output:
        ```
        Saved working directory and index state On main: Add file 1
        ```
    + ```git stash -u```: Stashes untracked (new) files beside tracked files.
    + ```git stash list```: Shows all the stashes you have saved. Example output:
        ```
        stash@{0}: On main: Add file 1
        ```
    + ```git stash apply``` / ```git stash apply stash@{N}```: Re-applies the last / specified stashed changes  without removing them from the stash list. Example output will be:
        ```
        Your branch is up to date with 'origin/main'.

        Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
            new file:   example/file_1.txt
        ```
    + ```git stash pop``` / ```git stash pop stash@{0}``` : Re-applies the last / specified stashed changes and removes them from the stash list.
    + ```git stash drop [stash@{N}]```: Removes a specific stash without applying it.
    + ```git stash clear```: delete all stashed changes in repository. After deleting, we can not retrive these changes anymore.


### 4. Git reset
### 5. Git revert
### 6. Git tag
### 7. Git reflog

