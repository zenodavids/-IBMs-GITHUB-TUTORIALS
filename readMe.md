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

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/distributed-repos.jpg)

This is used to take an existing project and make it the **starting point** for your new project

### Cloning a Project

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/clone-origin.jpg)

creates a copy of a repository on your local machine

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/repo-code.jpg)
![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/code-clone-url.jpg)

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

#### Say new Developer joins a new team and wants to collaborate on the Team's project,

This developer can create a identical copy of the remote repo using the **git clone** operation. The remote repo from which the main project is originally cloned from is also referred to as the **origin**.

After cloning the repo to the local machine, the developer can start making changes to the codebase. This could be for tasks like adding features and enhancements or fixing bugs. Typically the developer would use **git branch** to create a branch, _e.g. feature1-branch_, make that branch active using **git checkout** and make changes within that branch - such as by adding or editing files. The developer saves their changes often within the branch by using **git add** followed by **git commit**.

Once the changes for a particular branch are complete, rather than **merging** to the main branch directly, it is often a good practice to **push** the new branch with changes to origin where other developers/reviewers can test/review the changes before merging the branch to main.

#### Every once in a while, a developer may want to get the latest copy of the repo from origin to serve as the base for making changes or reviewing changes by others.

For example, this may be the case after the changes in _feature1-branch_ have been pushed to origin and the peer developer wants to review the code. The **git fetch** command can be used for this purpose.

The **git diff** command can help others reviewing your code to to identify and compare the changes. Once a peer reviewer or project maintainer has reviewed the changes, and is satisfied, the reviewer will **git checkout** the main branch and then **git merge** the new _feature1-branch_, which can then be deleted. After the branch is merged locally, the reviewer can **git push** the updated main branch back to origin.

> NOTE: The git-remote -v command can be used to check which remote repos you are synchronizing push and fetch changes with.

Another option for getting the latest copy of the repo is to use the **git pull** command. _The pull command in effect is a combination of fetch and merge_. That is, using this single command, you can both fetch and merge the changes into your local repo. For example, another developer who wants to use the updated codebase with the feature1 changes that have been merged to main branch in origin, can use the **git pull** command to fetch the updated codebase from origin and merge with his/her local codebase before starting development on a new feature.

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/clone-workflow.jpg)

### Forking a Project

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/fork.jpg)

- Takes a copy of a Github repo to use it as a base for a new project without affecting the original project.
- You can also use forking to submit changes back to the original repo.
- also used to independently make changes to a project.

> NOTE: The fork option is available only using the web interface and there is no git command to create a fork.

- submit a pull request to the original owner and owner decides whether or not to accept your changes.

- **_Origin_** refers to your Fork
- **_Upstream_** refers to the original work

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

![Alt text](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0131EN-SkillsNetwork/labs/reading-fork-clone/images/fork-workflow.jpg)

### Other commands for managing forks

- To grab **upstream** branches
  ```s
  git fetch upstream
  ```
- To merge changes into the main branch
  ```s
  git merge upstream/main
  ```

### When to fork or clone?

Typically if you have access to a project repo e.g. as part of a team developing a codebase collaboratively, you can **clone** the repo and synchronize changes from your local copy of the repo using pull and push.

If however there is a public project that you want to contribute to but do not have write access to, or use a public project as a starting point for your own project, you can **fork** the project. Then work with the forked codebase by cloning it to your machine and collaborating with your development team working on the fork using the pull-push synchronization with your fork of the project. But if you want to contribute your changes back to the upstream project (the original project that you forked from), you can submit your changes using a pull request.

# Managing Github Projects

Below are roles involved in managing a project;

### 1. GitHub developer

A developer communicates with other developers using these commands;

```s
git clone [repository clone URL]
```

download a copy of the main project to a local machine

```rust
git pull /*and*/ git fetch /*from the "origin"*/
```

keeps up-to-date with the upstream

```s
git push
```

push your changes to a shared repository if you adopt CVS shared repository workflow

```s
git format patch
```

to prepare email submission if you adopt linux cornell's style workflow

```s
git send email
```

to send your email submission without corruption by your MUA

```s
git request pull
```

to create a summary of changes for your upstream to pull

### 2. GitHub Integrator

An integrator plays the following roles;

- receives changes made by others
- reviews and responds to pull requests and,
- publishes the result for others to use.

Integrators use the following commands;

```s
git am
```

to apply patches emailed in from your contributors

```s
git pull
```

to merge from your trusted lieutenants

```s
git format patch
```

to prepare and send suggested alternatives to contributors

```s
git revert
```

undo botched commits

```s
git push
```

to publish the bleeding edge

### GitHub Repository Administrator

the repo administrator sets up and maintain access to the repository by developers.
they use the following commands;

```s
git daemon
```

allow anonymous download from repository

```s
git shell
```

can be used as a restricted login shell for shared central repository users

```s
git http backend
```

provides a server-side implementation of Git-over-Http(_smart http_) allowing both **fetch** and **push** services

```s
gitweb
```

provides a frontend to git repositories, which can be set-up using the **git-instaweb** script
