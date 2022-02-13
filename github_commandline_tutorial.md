# Getting Started with GitHub

If you’re getting started with GitHub, you’ve come to the right place! We’ll take a step-by-step approach to unpacking
the world of GitHub to get you started on project collaboration and version control with git.

For this tutorial, we’re assuming you’ve set up git on your computer. If you haven’t yet, simply follow
[this guide](https://docs.github.com/en/get-started/quickstart/set-up-git) then find your way back here. We'll be using
the command line to connect to GitHub.

You'll need to make a GitHub account. If you haven't yet set up a GitHub account, go to [GitHub](https://github.com) and set one up by going to the "Join
GitHub" and opting to make a new account.

If you have a repository you've already made and are looking to add it to GitHub, follow the **Adding a Local Repository 
to GitHub** section. Otherwise, if you're looking to contribute to an existing GitHub project, following the 
**Downloading a GitHub Repository** section.

<details>
    <summary><font size="+2"><b>Adding a Local Repository to GitHub</b></font></summary>

First off, you'll need to add a repository to your GitHub account which will be your remote repository.

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

Next, move on to the **Working with GitHub** section.

</details>

<details>
    <summary><font size="+2"><b>Downloading a GitHub Repository</b></font></summary>

First off, you’ll need to find the project you want to download from GitHub. Go to [github.com](https://github.com) and
navigate to your desired project page. Click on the green _Code_ button at the top right corner of the page and copy
the URL under HTTPS. Note, you may need to first "fork" the repository. If this isn't your repository, then Click the 
_Fork_ button at the top right corner first, navigate to your repositories, and then click on the green _Code_ button and 
get the HTTPS URL.

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

Next, move on to the **Working with GitHub** section.

</details>






<details>
    <summary><font size="+2"><b>Working with GitHub</b></font></summary>

You've made it here, so either you've added a local repository to GitHub or downloaded a GitHub repository, meaning
you're ready to get started working with GitHub!

Say now you're working on some code which you have yet to commit. You've made some progress, but you're not quite yet
ready to make the jump to committing your code. Now, all of a sudden, you need to switch gears entirely and work off
code from your latest commit. You don't want to lose all your progress, but you're not ready to commit your work while 
you switch gears either. What do you do?

Well, you're in luck. Git **Stashing** is here to save the day!

### Stashes

Stashing changes is the act of temporarily removing (or stashing) changes to your working repository, which you can
later choose whether to keep or discard. Stashing happens after adding changes but before committing them. Stashing
is especially important for when you're working on something you'd like to hold onto but aren't ready to commit.
Stashing does not prohibit continuing to change files - you can change branches or add changes with no harm. In fact,
it's just this that makes stashing so useful as we saw above.

Let's practice stashing.

Make some changes to your code in your current repository. Now, stash your current changes with the command:
```
$ git stash
```

You can have multiple stashes at a time. Now write some more code and again stash this new code with the command:
```
$ git stash
```

Now, let's view all your stashes. To view all your stashes, run:
```
$ git stash list
```
Each stash will have a unique identifier listed here. See all the ids?

With Stashing, if you've decided you're ready to apply your stash and remove the changes from there, you simply run the 
command ```git stash pop```, and you're changed files will be re-applied. Let's try it out. Now run:
```
$ git stash pop
```
Notice what happened? By default, ```git stash pop``` will apply the most recent stash. If you have multiple versions 
and want to apply a specific one, you pass the stash identifier found when listing the stashes. Let's list your stashes 
once more:
```
# git stash list
```
Grab the identifier for our original stash. Now run:
```
$ git stash pop <identifier>
```
where 'identifier' is replaced with the unique identifier we just grabbed. Now the original stash has been applied!

Let's say you want to reapply your changes, but you don't want to lose your stash. Maybe you're working on some code 
you'll have to stash away again soon, so there's no point in removing the stash. Well, you can use ```git stash apply```. 
Write some new code in your repository and, again, stash it. Now, simply run the command:
```
$ git stash apply
```
You got your code back! Now run:
```
$ git stash list
```
Notice how the stash is still there?

Again, this ```git stash apply``` will default to applying the most recent stash. You can pass a stash identifier at 
the end to specify a specific stash.

To remove all your stashes, use ```git stash clear```, or to remove just a particular stash, use
```git stash drop <identifier>```. Let's try this out. Run:
```
$ git stash clear
```
then run:
```
git stash list
```
Notice how all the stashes are gone?

Now, let's move onto **Branches**.

Let's say you and a friend want to work on a project together. You can't share the same local repository since you want 
to work on your own PCs, so how do you do this? The answer is: with branches.

### Branches

Branches are, in essence, an independent version of your repository with its own isolated code changes. Branches can be 
used to work on different features in isolation from other changes being made to the root repository. A repository can 
have many branches, allowing for the development of different features by different developers, experimentation, or 
creating separate use-cases. In this way, branches can be used for version control, with each branch specifying a 
certain version, or any other number of use cases.

A branch is always made from a pre-existing branch. Branches can be called from one another to merge changes and
integrate.

There is always a default, "main" branch that is the original branch made when the GitHub project was created. 
Let's use them!

To create a new branch in your local repository from your current branch, we run the command:
```
$ git branch <new-branch-name>
```
where 'new-branch-name' is replaced with the name you're assigning to your new branch. Let's call it 
'my-tutorial-branch' for our case.

* In the terminal navigate to the root directory for your repository and run the command:
```
$ git branch my-tutorial-branch
```

Note, if you wish to create a new branch from a branch other than the one you currently have checked-out, you can do so 
with the command:
```
$ git branch <new-branch-name> <target-branch>
```
where 'target-branch' is the name of the branch you want your new branch to be based off of.

Now, let's make a branch for your friend to use. We'll call it 'friend-tutorial-branch'.

* Run the command:
```
$ git branch friend-tutorial-branch
```

We're not quite yet done. To actually use the branch we created for ourselves, we need to check it out and push it to 
the remote repository.

To "checkout" a branch, we use the command:
```
$ git checkout -b <new-branch-name>
```
This is the general command to "checkout" a branch and can be used to "checkout" any existing branch.

Let's checkout this new branch.

* In your terminal, run:
```
$ git checkout -b my-tutorial-branch
```

To push a branch to GitHub, we use the command:
```
$ git push origin <new-branch-name>
```

* In your terminal, run:
```
$ git push origin my-tutorial-branch
```

Now repeat the process for the 'friend-tutorial-branch'. Go to [GitHub](https://github.com) and look at your project. 
Go to the "branches" section and notice how you now have two new branches: 'my-tutorial-branch' and 
'friend-tutorial-branch'.

Now that your new branch is a part of the remote repository, it can be downloaded and accessed from there. To write 
code on your new branch, simply check it out as we practiced before.

Checkout the 'my-tutorial-branch' branch. Write some code. To add this code to GitHub, we'll now follow a series of 
steps in the following order:

1. git add
2. git commit
3. git push

```git add``` essentially prepares your file to get committed to your local repository copy. This command is called 
**staging**. To learn more about staging, read the **Git Stage** section under **Basic Git Commands**.

As we said, first off, we'll stage your changes. In your terminal navigate to your project and run:
```
$ git add .
```
This will add all the changed files in your project.

Next, we need to commit the files to our local repository. In your terminal now run:
```
$ git commit -m my-first-commit
```
This will commit your changed files to your local repository with the tag 'my-first-commit'. Learn more about 
committing by reading the **Git Commit** section under **Basic Git Commands**.

Finally, we need to push our changes to the remote repository. The push command uploads your local commits to the 
remote repository. In your terminal now run:
```
$ git push origin my-tutorial-branch
```
Go to GitHub and navigate to your branch. You'll see a new 'commit'. Click on it, and you'll see all the changed files 
what was changed!

Now, checkout your 'friend-tutorial-branch' branch by running:
```
$ git checkout -b main
```
Add some code change(s) that differ from your changes to 'my-tutorial-branch', and repeat the process of add, commit, 
push.

Now, let's say you want to consolidate the changes between these two branches. There are two ways for handling this: 
```git rebase``` and ```git merge```. For this tutorial, we'll be using ```git merge```, but we'll talk about rebasing 
as well.

#### Merging

Merging is the one of two methods in GitHub to consolidate changes between branches, or forked history. It takes the 
changed lines created in each branch and integrates them into one branch. In essence, the merge command combines 
sequences of commits into a single history. The merge, as mentioned earlier, only affects the current branch where the 
merge command is being called, not the remote branch being referenced.

Merging is accomplished with the command:
```
$ git merge <branch-name>
```
where 'branch-name' is the remote branch's name.

Let's try it out!

In your terminal, navigate to the root directory of your project repository and checkout the 'my-tutorial-branch':
```
$ git checkout -b my-tutorial-branch
```

Now merge the 'friend-tutorial-branch' into your current branch:
```
$ git merge friend-tutorial-branch
```

Look at your project. Notice any changes? The 'friend-tutorial-branch' branch changes should now be integrated. Hooray!

Read **Git Rebase** under the **Basic Git Commands** section to learn about rebasing.

I hope you enjoyed this tutorial and learned about the use and importance of GitHub. Happy coding!


</details>





<details>
    <summary><font size="+2"><b>Basic Git Commands</b></font></summary>

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

where 'branch-name' is the name of the branch you wish to push to.

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
where 'branch-name' is the remote branch's name.

### Git Pull

The pull command is used to fetch and download changes from the remote repository to the local repository, essentially
combining the git fetch and git merge functions. Upon download, a merge workflow will be created to merge the content.
Git pull is achieved with the command ```git pull```:
```
$ git pull origin <branch-name>
```
where 'branch-name' is the name of the branch you wish to pull into your local repository.

### Git Rebase

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

</details>

