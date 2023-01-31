# Getting started

## Short Glossary of Terms

- **SSH protocol** : A method for secure remote login from one computer to another
- **Repository** : The folders of your projects that are set up for version control
- **Fork** : A copy of a repository -** Pull request** : The process you use to request that someone reviews and approve your changes before they become final.
- **Working directory** : A directory on your file system including files and sub-directories, that's associated with a repository
- **Remote repository** - a version of a project that is stored on a remote server and can be accessed by multiple people.

## Basic Git Commands

```s
git init
```

To be created once when starting o new repository

```s
git add .
```

move changes from all the files from the **working directory** to the **staging area**

```s
git add filename.fileExtension
```

move changes from a particular file from the **working directory** to the **staging area**

```s
git status
```

allows you to see the state of your **working directory** and takes snapshots of your changes

```s
git commit -m "commit message"
```

let's you takes snapshots of your changes and commits(adds) them to the projects.
**-m** stands for **message**
**"commit message"** is to take note of the changes you made at that stage.

```s
git reset
```

let's you undo changes that you've made to the files in your **working directory**.

```s
git log
```

let's you browse through previous changes in your project

```s
git branch
```

let's you creates an isolated environment within your repository to make changes

```s
git checkout
```

let's you see and change existing branches

```s
git merge
```

let's you put everything back together again

To learn more about Github, download the (cheat sheet 📜)[https://gist.github.com/cferdinandi/ef665330286fd5d7127d]

### Github Branching

```s
git branch
```

show list of all branches (the branch marked "\*" is the current branch you're on)

```s
git checkout -b linux-work
```

create a new branch named "linux-work"

#### Making changes in Branching

```s
git checkout master
```

go back to master branch

```s
git branch -m <oldName> <newName>
```

rename branch

```s
git branch -m <newName>
```

rename current branch

### Pull request

- A pull request makes the proposed (committed) changes available for others review and use.
- Pull request can follow any commit even if the code is unfinished.
- Github automatically makes a pull request if you make changes on a branch you do not own.
- log files record the approval of the merge.

### Merge Pull Request

- the master branch should be the only deployed code.
- Developers can change the source files in a branch but changes are not released until;
  - they are committed,
  - a pull command is issued,
  - the code is reviewed and approved
  - the approved is merged back into the master code.

## A quick guide to Pulling and Merging

- Clone the repository to your local machine.

- Create a new branch

  _Create a new branch called **linux** and get into the new branch_

  ```s
  git checkout -b linux
  ```

  _creates another new branch called **linux-baby** from the new linux branch_
  _this method is safest - create a branch, and a branch of the newly created branch._

  ```s
  git checkout -b linux-baby linux
  ```

- Make the changes to the files in the child branch **(linux-baby)**.

- Stage the changes using the command
  _for one file_

  ```s
  git add [file-name]
  ```

  _for everything_

  ```s
  git add .
  ```

- Commit changes to the child branch

  ```s
  git commit -m "commit-message in present tense"

  ```

- Push the changes to the remote branch using the command

  ```s
  git push origin linux-baby

  ```

- Open a pull request

  - Go to the Github repository where the changes were pushed.
  - Navigate to the **Branches** tab.
  - Find the branch you pushed changes to and click on it.
  - Click the **New pull request** button to open a new pull request.
  - Choose the base branch and the compare branch. **The base branch(linux) is the branch you want to merge the changes into and the compare branch (linux-baby) is the branch you pushed changes to**.
  - Add a descriptive title and optional description to the pull request.
  - Review the changes made in the pull request.
  - If everything looks good, click the **Create pull request** button.

- Merge a pull request into the main branch
  - The pull request will now be open for review and discussion by other collaborators. If there are any changes or suggestions, you can make the necessary changes and push them to the same branch.
  - Once all necessary changes have been made, and the pull request has been approved, you can merge the changes into the base branch.

After you've successfully opened a pull request and merged changes into the base branch, there are a few steps you can take to clean up your repository and maintain good version control practices:

- Fetch the latest changes from the remote repository to your local machine

  ```s
  git fetch origin
  ```

- Checkout to the base branch using the command "git checkout [base-branch-name]".

  ```s
  git checkout [base-branch-name]
  ```

- Pull the latest changes from the remote repository

  ```s
  git pull origin [base-branch-name]
  ```

- Delete the branch you used for the pull request, if it's no longer needed.

  ```s
  git branch -d [compare-branch-name]
  ```

- Repeat these steps on any other local machines where you have cloned the repository, to keep them up-to-date with the latest changes.

- By keeping your repository clean and up-to-date, you'll be able to more easily track changes and collaborate with others on your projects.

# Team working with Github

## Cloning and Forking a project

This is used to take an existing project and make it the **starting point** for your new project

### Cloning a Project

creates a copy of a repository on your local machine

**When working with a team** ;

- Clone the team's repository

  ```s
  git clone [repository clone URL]
  ```

- When you've made your changes and ready to sync the code back to github;

  - first, add the changed files to the **staging area**. this is the area where commits can be formated and reviewed before completing the commit
    ```s
    git add .
    ```
  - once you are ready to commit the changes in the staging area,

    ```s
    git commit -m "commit message in present tense"
    ```

  - To transfer your changes from your local machine's repository to the online Github repository,

    ```s
    git push
    ```

  - To transfer any changes from the online Github repository to your local machine's repository,

    ```s
    git fetch
    ```

    **_note that it does`nt merge those changes to the branch you're working on. you can merge them manually_**

  - To **transfer** any changes from the online Github repository to your local machine's repository and **merge** the changes to a branch,

    ```s
    git pull
    ```

    _git pull = git fetch + git merge_

### Forking a Project

- Takes a copy of a Github repo to use it as a base for a new project without affecting the original project.
- You can also use forking to submit changes back to the original repo.
- also used to independently make changes to a project.
  - submit a pull request to the original owner and owner decides whether or not to accept your changes.

**_Origin_** refers to your Fork
**_Upstream_** refers to the original work

**To keep a fork in sync with the original work from a local clone** means to regularly update your fork with the latest changes made in the original repository.(_This is often done when you have forked a repository to make your own changes, but still want to incorporate changes made by others to the original repository._),

- Fork the original project
- create a local clone of the project(repo)
  ```s
  git clone [forked repository clone URL]
  ```
- to configure Git to sync your fork, open the terminal and change to the directory containing the clone;

  - To access the remote repository

    ```s
    git remote -v
    ```

  next,

  ```s
  git remote add upstream [forked repository clone URL]
  ```

  to see the changes,

  ```s
  git remote -v
  ```

### Other commands for managing forks

- To grab **upstream** branches
  ```s
  git fetch upstream
  ```
- To merge changes into the main branch
  ```s
  git merge upstream/main
  ```
