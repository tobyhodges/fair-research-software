---
title: Version control
teaching: 60
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a version control system?
- How can a version control system help make my work reproducible?
- What does a standard version control workflow look like?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create atomic commits in git to incrementally save work
- Create branches to separate development work from stable work
- Push new work from a local machine to a remote server
- Open Pull Requests to review and merge new work into the stable branch

::::::::::::::::::::::::::::::::::::::::::::::::

### Create a new repository

Create a new directory in the `Desktop` folder for our work, and then change the current working directory to the newly created one:

```bash
$ cd ~/Desktop
$ mkdir planets
$ cd planets
```

We tell Git to make `planets` a repository -- a place where Git can store versions of our files:

```bash
git init
```

We can check everything is setup correctly by asking Git to tell us the status of our project:

```bash
$ git status
```

```output
On branch main
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

The exact wording of this output may be slightly different if you are using a different version of Git.

### Create and update file

Let's create a file called `mars.txt` that contains some notes about the red planet.
We will use the `touch` command to create the file, and then open and edit it in VSCode.

```bash
$ touch mars.txt
```

Type the below text into the `mars.txt` file:

```output
Cold and dry, but everything is my favourite colour
```

If we check the status of our project again, Git tells us that it's noticed the new file:

```bash
$ git status
```

```output
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	mars.txt

nothing added to commit but untracked files present (use "git add" to track)
```

The "untracked files" message means that there's a file in the directory that Git isn't keeping track of.
We can tell Git to track a file using `git add`:

```bash
$ git add mars.txt
```

and then check the right thing happened:

```bash
$ git status
```

```output
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   mars.txt
```

Git now knows that it's supposed to keep track of `mars.txt`, but it hasn't recorded these changes as a commit yet.
To get it to do that, we need to run one more command:

```bash
$ git commit -m "Start notes on Mars"
```

```output
[main (root-commit) 6045e0d] Start notes on Mars
 1 file changed, 1 insertion(+)
 create mode 100644 mars.txt
```

When we run `git commit`, Git takes everything we have told it to save by using `git add` and stores a copy permanently in a special `.git` directory.
This permanent copy is called a commit (or revision).

We use the flag `-m` (for message) to record a short, descriptive, and specific comment that will help us remember later on what we did and why.
If we just run `git commit` without the `-m` option, Git will launch a text editor so that we can write a longer message.

Good commit messages start with a brief (<50 characters) statement about the changes made in the commit.
Generally, the message should complete the sentence "If applied, this commit will".
If you want to go into more detail, add a blank line between the summary line and your additional notes.
Use this additional space to explain why you made changes and/or what their impact will be.

If we run `git status` now:

```bash
$ git status
```



## Acknowledgements

The content of this episode was inspired / heavily borrowed from the following resources:

- ...
- ...

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- ...
- ...




:::::::::::::::::::::::::::::::::::::::: keypoints

- A version control system is software that tracks and manages changes to a project over time
- Using version control aids reproducibility since the exact state of the software that produced an output can be recovered
- A commit represents the smallest unit of change to a project
- Branches are an integral part of the version control workflow since they separate stable work from developing work, and limit conflicts between collaborators
- Pull Requests are a mechanism to include changes into the stable branch after passing tests and code review

::::::::::::::::::::::::::::::::::::::::::::::::::
