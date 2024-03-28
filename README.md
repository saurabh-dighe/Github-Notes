# Git

![letsLearnGit](images/git.png)

git is a product from Linus Torwarlds, the same person who is a major contributor and founder of LINUX

### Important Notes and commands related to GIT 

## git : Is a local version control system 
## github, bitbucket, gitlab are the Central Version Systems 

#### What is GIT ?

```
Git is a version control system used by almost all the organizations to version control their development and parallel development using branches.
```

#### What is a branch in GIT ?
```
    A branch is a copy of the code which allows the developers to test without touching the main code and this helps multiple developers to contribute parallely.

    By default, main is the branch which should be the source of truth or production ready code.
```
 
 #### How can you control parallel development and how multiple developers can contribute and develop the code parallely ?

 ```
    A branch is a version of your repository, or in other words, an independent line of development. A repository can contain multiple branches, which means there are multiple versions of the repository.

    Among all, main / master branch is something which you should always a checkout to create a new /feature branch
```



### Git Branch Naming Strategy 

```
Branching Naming Strategy will be based on the organizational standards.  

And based on what you're working on, name should define that.

Typically, either you work on  :
    a)  feature       [ feature/payment-enhancement ,  feature/password-auth ]
    b)  hotfix        [ hotfix/defect-correction ]
    c)  bug           [ bug/payments-correction ]
```

Hotfixes are used to addess quick correction of a bug or a defect usually to expedit the process and place corrections on prod straight away.


### Common Git Commands

```
    $ git branch                                            // shows you which branch you're on right now 
    $ git branch branchName                                 // Creates a branch with a name brancName by taking your branch code as a source 
    $ git checkout branchName                               // Switches your branch to branchName 
    $ git checkout -b branchName                            // Creates branch and switches to the branch
    $ git pull origin branchName                            // origin represents remote repository
    $ git push origin branchName                            // pushes changes to remote repository
    $ git fetch origin branchName                           // Downloads the changes, but they won't be applied, they will stay in staging
    $ git merge                                             // Downloaded changes will be applied


```

### Git Fetch vs Git Pull 

```
The key difference between git fetch and pull is that git pull copies changes from a remote repository directly into your working directory, while git fetch does not. The git fetch command only copies changes into your local Git repo and if you want to merge your changes fetched by git fetch, switch to the branch of your choice and then do a git merge. The git pull command does both
```


### PS :

```
Whenever you push any changes and if they look good and stable on main branch, then you will raise/create a create a Git Tag.

Git Tag : Creating a name to a commit, which can referenced later and using that we can make the software.

Git and Linux are like oceans, infinite things are there to learn. Both of them are created by the same person : Linux Torvolds.
```


#### GIT Has Branch Protection Rules Enabled to ensure you cannot push your changes directly to the MAIN Branch and always changes has to go through Pull Request only.

### Command to give a name in your commit history 

```
        git config --global user.name "CodingManoj"
        git config --global user.email "CodingManoj@gmail.com"
```


## V.Important Git Options That are commonly used

To see the list of commits 

    ```$ git log ```

# To see the list of only last 3 commits

    ```$ git log -n 3 ```

# To see the list of only last 3 commits along with the changes against those commints ? -p Shows the actual code changes introduced in each commit.

   ```$ git log -n 3 --stat -p```


# How to move between the commits ? 

``` Replace <commit-hash> with the actual commit hash you want to switch to. This will bring your working directory to the state it was in at that specific commit. 

    $ git checkout <commit-hash>     ( Detaching HEAD to the Previous Commit )

```
!!! Important Note:

    *   Be cautious with detached HEAD. You're not technically on a branch, and any changes you make won't be tracked by Git until you switch back to a branch.
    *   To return to a branch after using detached HEAD, you need to explicitly check it out again using git checkout <branch-name>.

# How to move to the previous commits on the branch or move to a previous stage on the same branch ?

###  Checking Out the Previous Commit on the Current Branch:

This approach keeps you on your current branch and moves the working directory to the state of the previous commit within that branch. It's suitable if you want to undo recent changes and continue working on the same branch.

Steps:

```
    1) Use "git log" to find the commit hash of the previous commit.

    2) Run "git reset --hard commitHash" 
```



# What is GIT STASH ?

Git stash is a powerful tool in Git that allows you to temporarily save your uncommitted changes and come back to them later with a clean working directory. It's particularly useful in the following scenarios:

### Switching Branches:

    Imagine you're working on a feature branch (feature/new-login) and need to switch to the master branch to fix a bug. You have uncommitted changes in your feature/new-login branch that you don't want to lose. Here, git stash comes to the rescue. You can:

   ```  
        $ git stash: This saves your uncommitted changes in a stash.
        $ git checkout master: Switch to the master branch with a clean working directory.
        Fix the bug on master.
        $ git checkout feature/new-login: Return to your feature branch.
        $ git stash pop: Apply the stashed changes back to your working directory.
     ```


# What is Git Fetch vs Git Pull and why would we need that ?

Both git fetch and git pull are essential commands in Git for managing remote repositories, but they serve different purposes:

`git fetch:`

Downloads the latest changes from a remote repository (usually the origin, which points to a remote server like GitHub) without integrating them into your local branch.

Updates your local copy of the remote branches (references) but doesn't modify your working directory or current branch.

Use it when you want to see what changes have been made on the remote repository without merging them into your local work.

### Example:

Let's say you're working on your local branch (feature/new-login) and want to know if there have been any updates on the remote master branch. You can run:

``` git fetch origin```

This will download the latest commit information and branch references from the remote origin (usually your GitHub repository) but won't affect your local branch or working directory.

### git pull:

```Combines git fetch and git merge in a single command.```


# What is Cherry Pick ?

Cherry-picking allows you to selectively pick a specific commit (or a few commits) from one branch and apply it to another branch. It's like transplanting a specific change from one place in your Git history to another.

### Purpose:

    * Merging specific changes from one branch into another without merging the entire branch history.
    * Useful for incorporating bug fixes, new features, or other isolated changes from one branch to another.

    Example : 

    ```
        Imagine you're working on a new feature branch called feature/new-login. 
        You've made several commits related to the login functionality. 
        However, you realize there's a critical bug fix committed on the master branch that you need to incorporate into your feature/new-login branch.

        Here's how cherry-picking can help:

        Identify the Commit Hash: Use git log on the master branch to find the commit hash of the bug fix you want to cherry-pick. Let's assume the hash is 1234abc.

        Cherry-Pick the Commit: Switch to your feature/new-login branch and run:

        
        git cherry-pick 1234abc


    ```
