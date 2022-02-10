## Getting Started with GitHub

If you’re getting started with GitHub, you’ve come to the right place! We’ll take a step-by-step approach to unpacking
the world of GitHub to get you started on project collaboration and version control with git.

For this tutorial, we’re assuming you’ve set up git on your computer. If you haven’t yet, simply follow
[this guide](https://docs.github.com/en/get-started/quickstart/set-up-git) then find your way back here. We'll be using
the command line to connect to GitHub.

### Intro to GitHub

GitHub is a host for version control using Git.

### Basic Git Commands

#### Git Stage

Staging a file is the process of preparing a file for a commit in Git. Staging is kept as a separate command from
commit to let you continue changing files and commit when you are ready, committing only part or all of these changed
files. Staging is done with the command **git add**:

```
git add <content>
```

where <content> is replaced by the file or folder you would like to stage.

#### Git Commit

Committing staged files will commit these files to your local repository.

#### Git Push

The push command uploads your local commits to the remote repository.

#### Git Pull

### Adding a Local Repository to GitHub

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

### Downloading GitHub Repositories

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

