---
title: "Tools and practices for research software development"
teaching: 60
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions

- What tools are available to help us work in a FAIR way?
- How do the tools fit together to enable FAIR research?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Identify some key tools for FAIR research
- Explain why these help us work in a FAIR way
- Install and run key tools on their own workstation

::::::::::::::::::::::::::::::::::::::::::::::::

In this course we will introduce you to a group of tools and practices that are commonly used in research to help your work in a FAIR way. You should already have these tools installed on your machine following the setup instructions. Here we will give an overview of the tools, how they help you achieve the aims of FAIR research software and how they work together. In later episodes we will describe some tools in more detail.

The table below summarises which tools help to meet which parts of the FAIR software guidelines.

| Tools and practices                         | Findable | Accessible | Interoperable | Reusable |
|---------------------------------------------|----------|------------|---------------|----------|
| Integrated development environment - VSCode |          |            |               | x        |
| Programming language - Python               |          | x          | x             | x        |
| Reproducible workflows - Bash shell         |          |            | x             | x        |
| Version control - Git                       | x        |            |               |          |
| Documentation                               | x        |            | x             | x        |
| License                                     |          | x          |               | x        |
| Citation                                    | x        |            |               | x        |
| Software repository - GitHub                | x        | x          |               |          |

## Writing your code

### Development environment

One of the first choices we make when writing code is what tool to use to do the writing.
You can use a simple text editor such as Notepad, a terminal based tool such as Vim or Emacs, or one of many Integrated Developmet Environments (IDEs) which give you the tools to write, run and debug your code and inspect the output all in one place. 
(Note that you should not use word processing software such as Microsoft Word or Apple Pages to write code - these tools are designed to create nicely formatted text for humans to read, so they may add or change formatting, or insert invisible characters that the programming language can't interpret. 
Try opening a Word document in Notepad to see an example.)

This is mostly a personal choice as an experienced user of any of these tools can write good, FAIR software efficiently, but IDEs are popular because they are designed specifically for writing and running code.
There are some language specific IDEs such as PyCharm, and some that can work with many languages like VSCode (Visual Studio Code). 
IDEs also have add-ons that provide extra functionality, such as checking you are code as you type (similar to a spell-checker in Word), highlighting when you are not following best practice, or even automatically generating bits of code for you.

::::::::::::::::::::::::::: instructor
At this point you could open the Python file or another file in VSCode to show all the squiggly lines suggesting improvements.
::::::::::::::::::::::::::::::::

In this course we will use VSCode, as it is free, available on Windows, Mac and Linux operating systems, and can be used with many programming languages. It gives us a single program in which we can:

- view our file system
- open many kinds of files
- edit, compile, run and debug code
- open a terminal to run command line tools or view code outputs

Please open the Python file and the data file in VSCode now.

### Programming language

The programming language you decide to use is most often following the conventions of your research field. For example, people in the astrophysical simulation community mostly use C++ or Fortran, while people working in astrophysical image analysis might use R or Python.
This is partly becaue they are doing very different tasks.
Solving large numbers of matrices or linear equations requires lots of memory and processing power, so using a lower level language that gives you more control and optimisation is helpful.
Small data analysis tasks require more interactive work, quicker experimentation with the code, and don't take as long to run so optimisation is not a key aim and using a non-compiled language with a good plotting library might be better.
Big data tasks might want to access GPU resources and think about how to read in huge data files, so you would find a language or framework that specialised in certain hardware.

In this course we will use Python because it is a free, general purpose, higher level language. This means anyone should be able to get a copy of Python on any machine.
It is one of the most used languages in the world so it has good support for general tasks like reading files and plotting graphs, and is used in many specialised fields so you can find libraries to add more specialised tools for your own research.

It will help your Accessibility and Reusability if people in your community know how to read and run the language you are using, but don't forget that you can also be a force for change!
If you think the community is using a tool that doesn't meet their needs, you can advocate for a new approach, start a working group to translate widely-used codes into a new language and help others learn with you.

## Running your code

### Command line

In VSCode and other IDEs you can often run the code by clicking a button or pressing soem keyboard shortcut.
If you gave your code to a colleague or collaborator they might use the same IDE or something different, so you can't guarantee that they will have the same buttons and shortcuts as you.

In the last lesson we mentioned that Interoperable software should use standard protocols so that it can integrate with oter tools
One of these standard protocols is the command line or shell.
This is one of the oldest ways of interacting with computers so many programs will have commandf line interfaces.
Command line languages such as Bash and Zsh allow you to group or chain commands together to build up complex workflows using several programs in different steps. They also use less resources than a graphical user interface like and IDE so are commonly used on high-performance computers and other shared systems where time, memory and processing power are expensive or in high demand.

In this course we will use the Bash shell, which is one of the most common and comes already installed on Mac and Linux operating systems.
You can create a command line interface to your program which will allow it to be run on any system that has a Bash shell, and allow users to change things like input and output files or choose different settings or parameters without editing your code.
With a command line interface, your code can be built into automated workflows so that the whole process from data gathering to analysis to saving publication-quality results can be written in one Bash script and saved and reused.

### Inputs and outputs



### Testing

## Sharing your code

### Documentation

### Version control

### Licences and citation

### Code repositories and registries

## Summary

### Findable

- Describe your software - README
- Software repository/registry - GitHub, registries
- Unique persistent identifier - GitHub commits/tags/releases, Zenodo

### Accessible

- Software repository/registry
- License
- Costs/subscriptions - dependencies/language?

### Interoperable

- Explain functionality - readme/docs
- Standard formats
- Communication protocols - CLI/API

### Reusable

- Document functionality/install/run
- Follow best practices where appropriate
- License
- Citation

## Checking your setup

::::::::::::::::::::::::::::::::::::: challenge

Run the following commands to check you have installed the tools listed in the Setup page. Compare the output with your neightbour and see if you can see any differences.

1. `echo $SHELL`
2. `pwd`
3. `whoami`
4. `python --version`
5. `which python`
6. `git --help`
7. `code`

Solution:

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: exercise

Open a terminal and look at the prompt. Compare what you see in the terminal with your neighbour, does it look the same or different?
What information is it telling you and why might this be useful? What other information might you want?

Hint: The prompt is the `$` character and any text that comes before it, that is shown on every new line before you type in commands.

Solution:

::::::::::::::::::::::::::::::::::::::::::::::::

## Acknowledgements

The content of this episode was inspired / heavily borrowed from the following resources:

- ...
- ...

## Further reading

We recommend the following resources for some additional reading on the topic of this episode:

- ...
- ...

:::::::::::::::::::::::::::::::::::::::: keypoints

- Automating your analysis with shell scripts allows you to save and reproduce your methods.
- Version control helps you back up your work, see how data and code change over time and identify which analysis used which data and code.
- Programming languages each have advantages and disadvantages in different situations. Use the correct tools for your own work.
- Integrated development environments (IDEs) automate many coding tasks, provide easy access to documentation, and can identify common errors.
- Testing helps you check that your code is behaving as expected and will continue to do so in the future or when used by someone else.

::::::::::::::::::::::::::::::::::::::::::::::::::
