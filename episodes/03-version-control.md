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
