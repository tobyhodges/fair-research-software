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
$ mkdir spacewalks
$ cd spacewalks
```

We tell Git to make `spacewalks` a repository -- a place where Git can store versions of our files:

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

### Add initial files into our repository

During the setup for this lesson, you will have been provided with two files:

- `bad code.py`
- `Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv`

We need to move these files into our git folder.
You can either drag and drop the files from a file explorer window into the left pane of the VSCode IDE, or you can use the [`mv` command](https://linuxcommandlibrary.com/man/mv) in the terminal.

```bash
mv /path/where/you/saved/the/file/bad\ code.py ~/Desktop/spacewalks/
mv /path/where/you/saved/the/file/Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv ~/Desktop/spacewalks/
```

Let's see what that has done to our repository by running `git status` again:

```bash
git status
```

```output
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv
	bad code.py

nothing added to commit but untracked files present (use "git add" to track)
```

This is telling us that Git has noticed the new files.
The "untracked files" message means that there's a file in the directory that Git isn't keeping track of.
We can tell Git to track a file using `git add`:

```bash
$ git add bad\ code.py
$ git add Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv
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
	new file:   Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv
	new file:   bad code.py
```

Git now knows that it's supposed to keep track of `bad code.py` and `Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv`, but it hasn't recorded these changes as a commit yet.
To get it to do that, we need to run one more command:

```bash
$ git commit -m "Add and example script and dataset to work on"
```

```output
[main (root-commit) a5fa618] Add and example script and dataset to work on
 2 files changed, 438 insertions(+)
 create mode 100644 Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv
 create mode 100644 bad code.py
```

When we run `git commit`, Git takes everything we have told it to save by using `git add` and stores a copy permanently in a special `.git` directory.
This permanent copy is called a commit (or revision).

We use the flag `-m` (for message) to record a short, descriptive, and specific comment that will help us remember later on what we did and why.
If we just run `git commit` without the `-m` option, Git will launch a text editor so that we can write a longer message.

Good commit messages start with a brief (<50 characters) statement about the changes made in the commit.
Generally, the message should complete the sentence "If applied, this commit will".
If you want to go into more detail, add a blank line between the summary line and your additional notes.
Use this additional space to explain why you made changes and/or what their impact will be.

If we run `git status` now, we see:

```bash
$ git status
```

```output
On branch main
nothing to commit, working tree clean
```

This tells us that everything is up to date.
If we want to know what we've done recently, we can ask Git to show us the project's history using `git log`:

```bash
$ git log
```

```output
commit a5fa618f9cc9699146ac738bb439b50da6b9917d
Author: Sarah Gibson <drsarahlgibson@gmail.com>
Date:   Thu Feb 8 14:12:44 2024 +0000

    Add and example script and dataset to work on
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Where Are My Changes?

If we run `ls` at this point, we will still see just two files, the script and the dataset.
That's because Git saves information about files' history in the special `.git` directory mentioned earlier so that our filesystem doesn't become cluttered (and so that we can't accidentally edit or delete an old version).

::::::::::::::::::::::::::::::::::::::::::::::::::

## Acknowledgements

The content of this episode was inspired / heavily borrowed from the following resources:

- [Software Carpentry's Git Novice lesson](https://swcarpentry.github.io/git-novice)

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- The full [Software Carpentry Git Novice lesson](https://swcarpentry.github.io/git-novice)
- [_The Turing Way_'s guide to version control](https://the-turing-way.netlify.app/reproducible-research/vcs)

:::::::::::::::::::::::::::::::::::::::: keypoints

- A version control system is software that tracks and manages changes to a project over time
- Using version control aids reproducibility since the exact state of the software that produced an output can be recovered
- A commit represents the smallest unit of change to a project
- Branches are an integral part of the version control workflow since they separate stable work from developing work, and limit conflicts between collaborators
- Pull Requests are a mechanism to include changes into the stable branch after passing tests and code review

::::::::::::::::::::::::::::::::::::::::::::::::::
