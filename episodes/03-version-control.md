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
- Inspect logs to review the history of work
- Push new work from a local machine to a remote server

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

### Make a change

Did you notice how when we were typing the Python script into the terminal, we had to add a slash before the space like this: `bad\ script.py`?
Using a backslash in this way is called 'escaping' and it lets the terminal know to treat the space as part of the filename, and not a separate argument.
However, it is pretty annoying and considered bad practice to have spaces in your filenames like this, especially if you'll be manipulating them from the terminal.
So let's go ahead and remove the space from the filename altogether and replace it with a hyphen instead.
You can use the `mv` command again like so:

```bash
$ mv bad\ code.py bad-code.py
```

If you run `git status` again, you'll see Git has noticed the change in the filename.

```bash
$ git status
```

```output
On branch main
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	deleted:    bad code.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	bad-code.py

no changes added to commit (use "git add" and/or "git commit -a")
```

:::::::::::::::::::::::::::::::::::::: challenge

### Add and commit the changed file

Using the Git commands demonstrated so far, save the change you just made to the Python script.

Remember, commit messages should be descriptive and complete the sentence "If applied, this commit will...".
You can also use `git status` to check the status of your project at any time.

:::::::::::::: solution

### Solution

To save the changes to the renamed Python file, use the following Git commands:

```bash
$ git add bad\ code.py bad-code.py
$ git status
```

```output
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    bad code.py -> bad-code.py
```

```bash
$ git commit -m "Replace space in Python filename with hyphen"
```

```output
[main ef3508f] Replace space in Python filename with hyphen
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename bad code.py => bad-code.py (100%)
```

### Advanced solution

We initially renamed the Python file using the `mv` command, and we than had to add *both* `bad-code.py` and `bad\ code.py`.
Alternatively, we could have used Git's own `mv` command like so:

```bash
$ git mv bad\ code.py bad-code.py
$ git status
```

```output
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    bad code.py -> bad-code.py
```

`git mv` is the equivalent of running `mv ...` followed immediately by `git add ...` of the old and new filenames, so the changes have been staged automatically.
All that needs to be done is to commit them.

```bash
$ git commit -m "Replace space in Python filename with hyphen"
```

```output
[main 20e7004] Replace space in Python filename with hyphen
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename bad code.py => bad-code.py (100%)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Commit messages

:::::::::::::::::::::::::::::::::::::: challenge

### Good commit messages

Read the two commit messages below. In pairs or small groups, discuss which
messages help you understand more about what the commit author did. What about
the commit messages do you find helpful or not?

1. ```output
   [main 7cf85f6] Change variable
     1 file changed, 1 insertion(+), 1 deletion(-)
   ```
2. ```output
   [main 8baf69d] Change variable name from columns to column_headers
    1 file changed, 1 insertion(+), 1 deletion(-)
   ```

:::::::::::::: solution

### Solution

Commit message (2) is the better commit message since it is more descriptive about
what the author did. This message could be improved further by adding a blank line
then further describing the change discussing, for example, why the variable name
was changed.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Atomic commits

:::::::::::::::::::::::::::::::::::::: challenge

### Understanding commit contents

Below are the `diff`s of two commits. A `diff` shows the differences in a file
(or files!) compared to the previous commit in the history so you can what has
changed. Compare these two commit `diff`s. Can you understand what the commit
author was trying to achieve in each commit? How many changes have they tried to
make in each commit? Discuss in pairs or small groups.

<!-- FIXME: Figure out if ```diff would show diff colours here -->
1. ```bash
    diff --git a/bad-code.py b/bad-code.py
    index e804094..ba6a0f9 100644
    --- a/bad-code.py
    +++ b/bad-code.py
    @@ -1,3 +1,7 @@
    +import json
    +import datetime as dt
    +import matplotlib.pyplot as myplot
    +
    #https://data.nasa.gov/Raw-Data/Extra-vehicular-Activity-EVA-US-and-Russia/9kcy-zwvn/about_data

    csvfile = open('Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv', 'r')
    @@ -13,7 +17,6 @@
            #print(thing)
            l[fieldnames[thing]] = line[thing]

    -    import json
        json.dump(l, jsonfile)
        jsonfile.write('\n')

    @@ -25,8 +28,6 @@
        data.append(json.loads(line))
    data.pop(0)

    -import datetime as dt
    -
    time = []
    date =[]

    @@ -49,7 +50,5 @@
    for i in time:
        t.append(t[-1]+i)

    -import matplotlib.pyplot as myplot
    -
    myplot.plot(date,t[1:])
    myplot.show()
   ```
2. ```bash
    diff --git a/bad-code.py b/bad-code.py
    index e804094..333ef14 100644
    --- a/bad-code.py
    +++ b/bad-code.py
    @@ -1,23 +1,25 @@
    +import json
    +import datetime as dt
    +import matplotlib.pyplot as myplot
    +
    #https://data.nasa.gov/Raw-Data/Extra-vehicular-Activity-EVA-US-and-Russia/9kcy-zwvn/about_data
    
    csvfile = open('Extra-vehicular_Activity__EVA__-_US_and_Russia_20240126.csv', 'r')
    -jsonfile= open('file.json', 'a')
    -fieldnames = ("EVA #", "Country", "Crew    ", "Vehicle", "Date", "Duration", "Purpose")
    +jsonfile= open('file.json', 'w')
    +fieldnames = ("EVA #", "Country", "Crew", "Vehicle", "Date", "Duration", "Purpose")
    
    for count in range(370):
        line = csvfile.readline().split(',')
    
    -    #dict
    -    l = dict()
    -    for thing in range(len(line[:7])):
    -        #print(thing)
    -        l[fieldnames[thing]] = line[thing]
    -
    -    import json
    -    json.dump(l, jsonfile)
    +    # Create an empty dictionary to store cleaned data in
    +    data = dict()
    +    for i in range(7):
    +        data[fieldnames[i]] = line[i]
    +    json.dump(data, jsonfile)
        jsonfile.write('\n')
    
    jsonfile.close()
    +csvfile.close()
    
    data=[]
    
    @@ -25,8 +27,6 @@
        data.append(json.loads(line))
    data.pop(0)
    
    -import datetime as dt
    -
    time = []
    date =[]
    
    @@ -49,7 +49,5 @@
    for i in time:
        t.append(t[-1]+i)
    
    -import matplotlib.pyplot as myplot
    -
    myplot.plot(date,t[1:])
    myplot.show()
   ```

:::::::::::::: solution

### Solution

The git `diff` presented in option (1) is cleaner. The author has only tackled
one thing: placing the import statements at the top of the file. This kind of
commit is much easier to review in isolation, and will be easier to track down
if [`git bisect`](https://git-scm.com/docs/git-bisect) is required.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Git logs

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

### Pushing to a Git server

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
- Commit messages describe what each commit contains and should be descriptive
- Logs can be used to overview the history of a project

::::::::::::::::::::::::::::::::::::::::::::::::::
