# GIT 

## 1. What is Git?

Git is a distributed version control system used to track changes made to a set of files by individuals or groups. It is a FOSS (free and open-source) tool that is widely utilized by companies due to its efficiency and speed.

Git allows the creation of parallel development branches, enabling you and your team members to work simultaneously on different project features and merge them later. By keeping track of the changes made to the project, you can easily revert to a previous version in case any issues arise.

- [Watch: What is Version Control?](https://git-scm.com/video/what-is-version-control)

## 2. Installing Git

### Windows:
[Git for Windows installer](https://gitforwindows.org/)

### Debian/Ubuntu:
```bash
$ sudo apt-get update
$ sudo apt-get install git-all
```

### Fedora:
```bash
$ sudo dnf install git-all
```

### Mac:
[git-osx-installer](https://sourceforge.net/projects/git-osx-installer/files/git-2.23.0-intel-universal-mavericks.dmg/download?use_mirror=autoselect)

Using Homebrew
```bash
$ brew install git
```

After installing git, you need to configure it by setting your global username and email:

```bash
$ git config --global user.name "Your username"
$ git config --global user.email "youremail@domain.com"
```

If you want to configure a different username and email for a specific repository, you can run the same commands inside the folder of the repository without adding the `--global` option.

## 3. Basic concepts

![Git operations](C:\Users\marti\Desktop\git-operations.png)

In Git you have three main states: the working directory, the staging area, and the Git directory (or local repository). You can also have a remote repository connected to your Git directory. 

The working directory is, in essence, a copy of your project version. Git stores a compressed copy of all your versions inside a hidden folder, and they are decompressed when you need to access them.

The staging area stores information about the changes that are about to be committed to the repository. 

The Git directory (or local repository) stores all the important metadata for your project: commits, remote repositories, logs, etcetera.

- [Read: What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)



## 4. Setting up a local repository

### Create new repository

When you begin a new project, you can create a new folder to store your Git repository, which is created with `git init`

```bash
mkdir projectfolder
cd projectfolder
git init
```

### See repository status

This command will show you which files have been recently modified inside the project folder.

```bash
git status
```


### Adding files to staging area

After creating and/or modifying the files from your working directory, you can add them all at once to the staging area using this command:

```bash
$ git add .
```

If you want to add a single file:

```bash
$ git add yourfilename
```

### Committing files from the staging area to the local repository

To commit all the changes to the local repository, you can use this command:

```bash
$ git commit -m "Your comment"
```

The comment should indicate what changes have been made to the repository. It's a good practice to write detailed messages that accurately represent the changes that have been made. If you type `git commit` without adding anything else, a text editor window will pop-up allowing you to write a message. The changes will commit to the local repository after you close the window.


## 5. Verifying changes in the local repository


### Checking what commits have been made

```bash
$ git log
```

### Checking what has been recently modified before a commit

After you modify a file, you will see it classified as "modified" after running `git status`. To see the changes that have been made since the last commit:
```bash
$ git diff
```


## 6. Branches

### See current branch

```bash
$ git branch
```

This command will print the branch you're currently working on.


### Create new branch

Verify that you do not have pending commits:
```bash
$ git status
```

Create new branch:

```bash
$ git checkout -b yournewbranchname
```

It's common practice to create new branches when you want to add a new feature to the project. You can name them as `feature/your-feature` where "your-feature" corresponds to the name of the feature you want to add.

### Move to another branch

To move from a branch to another:

```bash
$ git checkout branchname
```

Where "branchname" is the branch you want to move to.

*NOTE: you can also use git-checkout to restore changed files to their latest version.*

- [Read: git-checkout docs](https://git-scm.com/docs/git-checkout)

### Merge branches

Let's say you have a branch that is several commits ahead from another. To merge that branch with your current branch:

```bash
$ git merge branchname
```

Where "branchname" corresponds to the branch you want to merge.

- [Read: git-merge docs](https://git-scm.com/docs/git-merge)


### Resolve merge conflicts

- [Read: Resolving a merge conflict using the command line](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)



## 7. Remote repositories

You can communicate with external repositories using Git. 

### Pushing an existing repository to a remote location

If you want to push to a remote repository, like one from Github:

```bash
$ git remote add origin git@github.com:username/repositoryname.git
$ git branch -M main
$ git push -u origin main
```

Where "username" corresponds to the owner and "repositoryname" is the name of the remote repository.

*TIP: you can replace "origin" with any other word you want, it's just an identifier.* 

### Clone remote repository to local

```bash
git clone repository-url
```

Where `repository-url` is the URL of the remote repository you want to clone inside your current directory.

### See configured remote repositories

```bash
$ git remote -v
```

### Retrieve changes from remote to local repository

To download changes from a single remote location:

```bash
$ git fetch origin
```

To download changes from all remote locations:

```bash
$ git fetch --all
```

- [Read: git-fetch docs](https://git-scm.com/docs/git-fetch)

### Fetch changes from remote and integrate them

*IMPORTANT NOTE: It is not recommended to use this command to download and integrate all changes from remote at once, unless you know there will be no conflicts. It's best to use git-fetch first.*

```bash
$ git pull origin
```

To integrate changes from all remote locations:
```bash
$ git pull --all
```

- [Read: git-pull docs](https://git-scm.com/docs/git-pull)


## 8. Best practices

Some free external resources for learning and applying Git best practices:

- [GitLab: What are Git version control best practices?](https://about.gitlab.com/topics/version-control/version-control-best-practices/)
- [Atlassian: Source code management](https://www.atlassian.com/git/tutorials/source-code-management)
- [Grant Weatherston: Git Best Practices - How to Write Meaningful Commits, Effective Pull Requests, and Code Reviews](https://www.freecodecamp.org/news/git-best-practices-commits-and-code-reviews/)



## Final notes

This article was created by Facundo Martínez © 2023. It is licensed under CC BY-NC-SA 4.0

If you have found it beneficial, kindly consider supporting me on [Github Sponsors](https://github.com/sponsors/fx-biocoder) or [Ko-fi](https://ko-fi.com/biocoder). Your contribution will assist me in creating more high-quality free content for the benefit of all.
