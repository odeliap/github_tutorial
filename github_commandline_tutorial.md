# Getting Started with GitHub

If you’re getting started with GitHub, you’ve come to the right place! We’ll take a step-by-step approach to unpacking
the world of GitHub to get you started on project collaboration and version control with git.

For this tutorial, we’re assuming you’ve set up git on your computer. If you haven’t yet, simply follow
[this guide](https://docs.github.com/en/get-started/quickstart/set-up-git) then find your way back here. We'll be using
the command line to connect to GitHub.

## Basic Git Commands

### Git Stage

Staging a file is the process of preparing a file for a commit in Git. Staging is kept as a separate command from
commit to let you continue changing files and commit when you are ready, committing only part or all of these changed
files. Staging is done with the command ```git add```:
```
$ git add <content>
```
where 'content' is replaced by the file or folder you would like to stage.

### Git Commit

Committing staged files will commit these files to your local repository. Git commit is achieved with the command ```git 
commit```:
```
$ git commit -m "commit_message"
```

Note, committing files does not commit them to your remote repository. To add changes to the remote repository, we use 
Git push.

### Git Push

The push command uploads your local commits to the remote repository. Git push is achieved with the command ```git push```:
```
$ git push origin <branch-name>
```

where 'branch-name' is the name of the branch you wish to push to. If you don't know what a branch is, just hang in 
there, we'll get to it soon.

### Git Fetch

The fetch command checks if there are any changed files in the remote repository, but it doesn't change any of your 
repository files. It is achieved with the command ```git fetch```:
```
$ git fetch <branch-name>
```
where 'branch-name' is the remote branch's name.

### Git Merge

The merge command allows for integration of changes made in another remote branch into your branch. It only changes the 
current branch, leaving the remote branch untouched. It is accomplished with the command ```git merge```:
```
$ git merge <branch-name>
```
where 'branch-name' is the remote branch's name. Since this is a complex topic, we'll get to it more in the 'Concepts' 
section.

### Git Pull

The pull command is used to fetch and download changes from the remote repository to the local repository, essentially 
combining the git fetch and git merge functions. Upon download, a merge workflow will be created to merge the content. 
Again, if you don't know total understand what merging is, we'll get to it in more depth soon! Git pull is achieved 
with the command ```git pull```:
```
$ git pull origin <branch-name>
```
where 'branch-name' is the name of the branch you wish to pull into your local repository.

## Key Concepts

Now we'll cover some important concepts to truly understand how Git and GitHub work.

### Stashes

Stashing changes is the act of temporarily removing (or stashing) changes to your working repository, which you can 
later choose whether to keep or discard. Stashing happens after adding changes but before committing them. Stashing 
is especially important for when you're working on something you'd like to hold onto but aren't ready to commit. 
Stashing does not prohibit continuing to change files - you can change branches or add changes with no harm. In fact, 
it's just this that makes stashing so useful.

To stash your current changes, you would simply run the command:
```
$ git stash
```

You can
have multiple stashes at a time. To view all your stashes, run:
```
$ git stash list
```
Each stash will have a unique identifier listed here.

If you've decided you're ready to apply your stash and remove the changes from there, simply run the command 
```git stash pop```, and you're changed files will be re-applied. By default, this will apply the most recent stash. If 
you have multiple versions and want to apply a specific one, pass the stash identifier found when listing the stashes:
```
$ git stash pop <identifier>
```

If you'd like to reapply your changes without removing them from your stash, simply run the command:
```
$ git stash apply
```

Again, this will default to applying the most recent stash. You can pass a stash identifier at the end to specify a 
specific stash.

To remove all your stashes, use ```git stash clear```, or to remove just a particular stash, use 
```git stash drop <identifier>```.

### Branches

We've already alluded to the idea of branches. Branches are, in essence, an independent version of your repository with 
its own isolated code changes. Branches can be used to work on different features in isolation from other changes being 
made to the root repository. A repository can have many branches, allowing for the development of different features by 
different developers, experimentation, or creating separate use-cases. In this way, branches can be used for version 
control, with each branch specifying a certain version, or any other number of use cases.

A branch is always made from a pre-existing branch. Branches can be called from one another to merge changes and 
integrate.

There is always a default, "main" branch that is the original branch made when the GitHub project was created.

* To create a new branch in your local repository from your current branch, use the command:
```
git branch <new-branch-name>
```
where 'new-branch-name' is replaced with the name you're assigning to your new branch.

* If you wish to create a new branch from a branch other than the one you currently have checked-out, you can do so with 
the command:
```
git branch <new-branch-name> <target-branch>
```
where 'target-branch' is the name of the branch you want your new branch to be based off of.

* To "checkout" this new branch, use the command:
```
$ git checkout -b <new-branch-name>
```
This is the general command to "checkout" a branch and can be used to "checkout" any existing branch.

* Next, you need to push it to GitHub with the command:
```
$ git push origin <new-branch-name>
```
Now that your new branch is a part of the remote repository, it can be downloaded and accessed from there.

### Rebasing

Rebasing is one of the two ways in GitHub to consolidate changes between branches. When different people work on 
different branches, their work diverges, and files changed in differing ways. What rebasing does is goes to the most 
recent ancestor for the branches' changed files, gets the differences from each incoming commit, saves those 
differences to temporary files, and then applies them to the branch being rebased to. Rebasing combines commits from 
two branches to a new base commit.

Rebasing is particularly important for maintaining the repository history in a chronological order.

Rebasing is accomplished with the command:
```
$ git rebase <base>
```


### Merging

Merging is the second method in GitHub to consolidate changes between branches, or forked history. It takes the changed 
lines created in each branch and integrates them into one branch. In essence, the merge command combines sequences of 
commits into a unified history. The merge, as mentioned earlier, only affects the current branch where the merge 
command is being called, not the remote branch being referenced.

Merging is accomplished with the command:

```
$ git merge <branch-name>
```
where 'branch-name' is the remote branch's name.


## Adding a Local Repository to GitHub

First off, you'll need to make a GitHub account and add a repository there which will be your remote repository. 
Once you've made this repository, under the **Code** tab, select a URL (you can use either the HTTPs, SSH, or Git CLI, 
but we'll be using HTTP for this tutorial) and copy it to your clipboard. This is your **remote repository URL**.

To add a local repository to GitHub, open a terminal and find your way to the project directory for the project
you wish to add. Make your root directory a GitHub repository with the command:

```
$ git init -b main
```

Next, you'll want to **stage** all your files and commit them to GitHub. Stage all the files in this directory to set 
up for committing them to GitHub:

```
$ git add .
```

Next, you'll need to **commit** all these staged files to GitHub. Commit these files with the command:

```
$ git commit -m "your-message"
```

where "your-message" should be replaced by any message of your choice, preferably one that hints at the files committed.

Now, you'll need to **add a remote repository URL** to your project to push your changes to the remote project.

A remote repository is a repository hosted online which holds your repository and all changes pushed to it. To add this
remote repository to your local machine for pushing changes to the remote, enter the commands:

```
$ git remote add origin <URL>
$ git remote -v
```

where origin is the remote-name and <URL> is replaced by the remote URL, with the format:
```https://github.com/username/repository-name```.

Now that your remote repository has been added to your local repository, you're ready to **push** your committed files to
the remote. To push your commits to your specified remote repository, enter the following command:

```
$ git push -u origin main
```

You're all done! If you've gotten to here, you've hopefully successfully added your local repository to GitHub.

## Downloading GitHub Repositories

First off, you’ll need to find the project you want to download from GitHub. Go to [github.com](https://github.com) and
navigate to your desired project page. Click on the green _Code_ button at the top right corner of the page and copy
the URL under HTTPS.

**Note**: You can also clone the repository using SSH or the GitHub CLI. For cloning the repository using SSH, the process is generally the same, except you’ll need to first
[add a public SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
to your GitHub account then copy the URL under SSH and following the instructions below, replacing the HTTPs URL with
your SSH one.

Once you’ve copied the URL to your clipboard, continue.

To download a GitHub repository, we will clone it from GitHub:

1)	Open your terminal
2)	cd to the directory where you’d like the repo to be downloaded to
3)	clone your repository by typing and entering the command:

```$ git clone https://github.com/username/repository-name```

where ```https://github.com/username/repository-name``` is the URL copied from earlier. The HTTP URL should follow this
format.

You're all done! You should see the repository cloned to your current directory. If you're having any troubles, refer
to [this page](https://docs.github.com/en/repositories/creating-and-managing-repositories/troubleshooting-cloning-errors).

