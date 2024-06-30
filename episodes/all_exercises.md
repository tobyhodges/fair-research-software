## Episode: "Course introduction"

### Exercise: 
### What does open and reproducible research mean to you?
Think about the questions below. Your instructors may ask you to share your answers in a shared notes document and/or 
discuss them with other participants.

- What do you understand by the words "open" and "reproducible" in the context of research?
- How many people or groups can you list that might benefit from your work being open and reproducible?
- How many times did you wish that someone else's work you came across was more open or accessible to you? 
Can you provide some examples?
## Episode: "FAIR research software"

### Exercise: 
### Motivation
Think about the questions below. Your instructors may ask you to share your answers in a shared notes document and/or
discuss them with other participants.

- What motivated you to attend this course? Did you come by choice or were you advised to attend?
- What do you hope to learn or change in your current research software practice? Describe how your knowledge, 
work or attitude may be different afterwards.


### Exercise: 
Think of a piece of software you use in your research - any computational tool used for data gathering, modelling & simulation, processing & visualising results or others. 
If you have a bit of code or software you wrote yourself, in any language, feel free to use that.

Think where on the FAIR spectrum it fits, using the following scale as a guide for each principle:

- 1 - requires loads of improvement
- 2 - on a good path, but improvements still needed
- 3 - decent, a few things could still be improved
- 4 - very good, only tiny things to improve upon
- 5 - excellent


### Exercise: 
Compare this data and code to the software you chose earlier.
Do you think it is Findable, Accessible, Interoperable and Reusable? 
Give it a score from 1 to 5 in each category, as in the previous exercise, and then we will discuss it together.

## Episode: "Tools and practices for research software development"

### Exercise: 
Open a command line terminal and look at the prompt. 
Compare what you see in the terminal with your neighbour, does it look the same or different?
What information is it telling you and why might this be useful? 
What other information might you want?

Run the following commands in a terminal to check you have installed the tools listed in the Setup page. 
Compare the output with your neighbour and see if you can see any differences.

Checking the command line terminal:

1. `date`
2. `echo $SHELL`
3. `pwd`
4. `whoami`

Checking Python:

5. `python --version`
6. `python3 --version`
7. `which python`
8. `which python3`

Checking Git and GitHub:

9. `git --help`
10. `git config --list`
11. `ssh -T git@github.com`

Checking VS Code:

12. `code`
13. `code --list-extensions`

::: hint

The prompt is the `$` character and any text that comes before it, that is shown on every new line before you type in 
commands.
Type each of the commands one at a time and press enter. 
They should give you a result by printing some text in the terminal.

## Episode: Version control

### Exercise: 
### Add and commit the changed file

Using the Git commands demonstrated so far, save the change you just made to the Python script.

Remember, commit messages should be descriptive and complete the sentence "If applied, this commit will...".
You can also use `git status` to check the status of your project at any time.


### Exercise: 
### Good commit messages

Read the two commit messages below. In pairs or small groups, discuss which messages help you understand more 
about what the commit author did.
What about the commit messages do you find helpful or not?

1. ```output
   [main 7cf85f6] Change variable
     1 file changed, 1 insertion(+), 1 deletion(-)
   ```
2. ```output
   [main 8baf69d] Change variable name from columns to column_headers
    1 file changed, 1 insertion(+), 1 deletion(-)
   ```


### Exercise: 
### Understanding commit contents

Below are the `diffs` of two commits. A `diff` shows the differences in a file (or files!) compared to the previous 
commit in the history so you can what has changed. 
The lines that begin with `+`s represent additions, and the lines that begin with `-`s represent deletions. 
Compare these two commit `diff`s. 
Can you understand what the commit author was trying to achieve in each commit? 
How many changes have they tried to make in each commit? 
Discuss in pairs or small groups.

1. ![Example Diff 1](fig/ex-diff-1.png)
2. ![Example Diff 2](fig/ex-diff-2.png)


To find out more about how to generate `diffs`, you can read the [Git documentation](git-diff-docs) or the [Tracking Changes episode][swc-git-lesson-track]
from the [Software Carpentry Version control with Git lesson][swc-git-lesson].


### Exercise: 
### Terminology

In pairs or small groups, discuss the difference between the terms `remote`
and `origin`. What is the definition of each term?

## Episode: Code readability

### Exercise: ### Give a descriptive name to a variable

Below we have a variable called `var` being set the value of 9.81.
`var` is not a very descriptive name here as it doesn't tell us what 9.81 means, yet it is a very common constant in physics!
Go online and find out which constant 9.81 relates to and suggest a new name for this variable.

Hint: the units are *metres per second squared*!

``` python
var = 9.81
```


### Exercise: ### Add some comments to a code block

Examine lines 7 to 20 of the `bad-code.py` script.
Add (or change!) as many inline comments as you think is required to help yourself and others understand what that code block is doing.

Hint: Inline comments in Python are denoted by a `#` symbol.


### Exercise: ### Create a function

Below is a function that reads in a JSON file into a dataframe structure using the [`pandas` library](https://pandas.pydata.org/) - but the code is out of order!
Reorder the lines of code within the function so that the JSON file is read in using the `read_json` method, any incomplete rows are *dropped*, the values are *sorted* by date, and then the cleaned dataframe is *returned*.
There is also a `print` statement that will display which file is being read in on the command line for verification.

``` python
import pandas as pd

def read_json_to_dataframe(input_file):
    eva_df.sort_values('date', inplace=True)
    eva_df.dropna(axis=0, inplace=True)
    print(f'Reading JSON file {input_file}')
    return eva_df
    eva_df = pd.read_json(input_file, convert_dates=['date'])
```


### Exercise: ### Writing docstrings

Write a docstring for the `read_json_to_dataframe` function from the previous exercise.
Things you may want to consider when writing your docstring are:

-   Describing what the function does
-   What kind of inputs does the function take? Are they required or optional? Do they have default values?
-   What output will the function produce?

Hint: Python docstrings are defined by enclosing the text with `"""` above and below. This text is also indented to the same level as the code defined beneath it, which is 4 whitespaces.

## Episode: "Code testing"

### Exercise: 
## Types of Software Tests

Fill in the blanks in the sentences below:

+ __________ tests compare the ______ output of a program to its ________ output
  to demonstrate correctness.
+ Unit tests compare the actual output of a ______ ________ to the expected output
  to demonstrate correctness.
+ __________ tests check that results have not changed since the previous test run.
+ __________ tests check that two or more parts of a program are working together correctly.


### Exercise: 
## What are the limitations of informally testing code? (5 minutes)
Think about the questions below. Your instructors may ask you to share your answers in a shared notes document and/or discuss them with other participants.

- What are the limitations of (only) using informat tests to verify that a piece of code is behaving as expected?


### Exercise: 
## Interpreting pytest output

A colleague has asked you to conduct a pre-publication
review of their code `Spacetravel` which analyses  time spent in space by
various individual astronauts.

Inspect the pytest output provided and answer the questions below.

### pytest output for `Spacetravel`

```output
============================================================ test session starts 
platform darwin -- Python 3.12.3, pytest-8.2.2, pluggy-1.5.0
rootdir: /Users/AnneResearcher/projects/Spacetravel
collected 9 items                                                                                                                                                              

tests/test_analyse.py FF...x                                              [ 66%]
tests/test_prepare.py s..                                                 [100%]

====================================================================== FAILURES 
____________________________________________________________ test_total_duration

    def test_total_duration():
    
      durations = [10, 15, 20, 5]
      expected  = 50/60
      actual  = calculate_total_duration(durations)
>     assert actual == pytest.approx(expected)
E     assert 8.333333333333334 == 0.8333333333333334 ± 8.3e-07
E       
E       comparison failed
E       Obtained: 8.333333333333334
E       Expected: 0.8333333333333334 ± 8.3e-07

tests/test_analyse.py:9: AssertionError
______________________________________________________________________________ test_mean_duration 

    def test_mean_duration():
       durations = [10, 15, 20, 5]
    
       expected = 12.5/60
>      actual  = calculate_mean_duration(durations)

tests/test_analyse.py:15: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

durations = [10, 15, 20, 5]

    def calculate_mean_duration(durations):
        """
        Calculate the mean of a list of durations.
        """
        total_duration = sum(durations)/60
>       mean_duration = total_duration / length(durations)
E       NameError: name 'length' is not defined

Spacetravel.py:45: NameError
=========================================================================== short test summary info 
FAILED tests/test_analyse.py::test_total_duration - assert 8.333333333333334 == 0.8333333333333334 ± 8.3e-07
FAILED tests/test_analyse.py::test_mean_duration - NameError: name 'length' is not defined
============================================================== 2 failed, 5 passed, 1 skipped, 1 xfailed in 0.02s 

```

a. How many tests has our colleague included in the test suite?
b. The first test in test_prepare.py has a status of s; what does this mean?
c. How many tests failed?
d. Why did "test_total_duration" fail?
e. Why did "test_mean_duration" fail?


### Exercise: 
## Write Unit Tests

Implement unit tests for the `calculate_crew_size` function. 
Cover typical cases and edge cases.


### Exercise: 
## Evaluating Code Coverage

Generate a code coverage report for the `Spacewalks` test suite
and extract the following information:

a.  What proportion of the code base is currently NOT exercised by the test suite?
b.	Which functions in our code base are currently untested?


### Exercise: 
### Exercise 1 - Typical Inputs

First, check that the function behaves as expected with 
typical input values. Fill in the gaps in the skeleton test below:

```python

def test_summarise_categorical_typical():
    """
    Test that summarise_categorical correctly tabulates
    distribution of values (counts, percentages) for a ground truth
    example (typical values)
    """
    test_input = pd.DataFrame({
        'country': _________________________________________, # FIX-ME
    }, index=[0, 1, 2, 3, 4])

    expected_result = pd.DataFrame({
        'country': ["Russia", "USA"],
        'count': [2, 3],
        'percentage': [40.0, 60.0],
    }, index=[0, 1])

    actual_result = ____________________________________________ # FIX-ME 
    
    pdt.__________________(actual_result, _______________) #FIX-ME

```


### Exercise: 
### Exercise 2 - Edge Cases

Now let's check that the function behaves as expected with edge cases.  
Does the code behave as expected when the column of interest contains one 
or more missing values (pd.NA)? (write a new test). 

Fill in the gaps in the skeleton test below:

```python
def test_summarise_categorical_missvals():
    """
    Test that summarise_categorical correctly tabulates
    distribution of values (counts, percentages) for a ground truth
    example (edge case where all column contains missing values)
    """
    test_input = _______________
    _______________
    _______________ # FIX-ME
    
    expected_result = _______________
    _______________
    _______________ # FIX-ME
    
    actual_result = summarise_categorical(test_input, "country")

    pdt.assert_frame_equal(actual_result, expected_result)
```    



### Exercise: 
### Exercise 3 - Invalid inputs

Now write a test to check that the `summarise_categorical` function raises an appropriate error 
when asked to tabulate a column that does not exist in the data frame


### Exercise: 
### Exercise 4 - Minimal Test Suite

Finally, let's add the `summarise_categorical` code and tests to 
the Spacewalks code base (eva_data_analysis.py).

a) Refactor the tests to use parameterisation where possible

b) What proportion of the code base is exercised by the test suite
after the new tests have been added?
    

## Episode: Documenting code

### Exercise: 
## READMEs and The FAIR Principles

Think about the question below. Your instructors may ask you to share your answer in a shared notes document and/or discuss them with other participants.

Here are some of the major sections you might find in a typical README. Which are **essential** to support the FAIR principles? Which are optional?

+ Purpose of the code
+ Audience (who the code is intended for)
+ Installation Instructions
+ Contribution Guide
+ How to Get Help
+ License
+ Software Citation
+ Usage Example
+ Dependencies and their versions
+ FAQs
+ Code of Conduct


### Exercise: 
## Spacewalks README

Extend the README for Spacewalks by adding
a. Installation instructions
b. A simple usage example

## Episode: My Software
## Episode: Spacetravel

### Exercise: 
## `Spacewalks` Software Citation

Write a software citation file for the Spacewalks code and add it to the root
folder of our project.

+ Add the URL of the code repository as a "Related Resources"
+ Add a one-line description of the code under the "Abstract" section
+ Add at least two key words under the "Keywords" section
+ Use the commit hash of your most recent commit to indicate the code
  version your citation file refers to.

## Episode: Spacewalks

### Exercise: 
## A `Spacewalks` How-to Guide

a. Review the Diataxis guidance page on writing a How-to guide. Identify
three features of an effective how-to guide.

b. Following the Diataxis guidelines, add a How-to Guide to the `docs` folder
that show users how to change the destination filename for the output dataset generated
by Spacewalks.


### Exercise: 
## A Spacewalks Tutorial

The Diataxis framework provides guidance for developing technical documentation
for different purposes. Tutorials differ in purpose and scope to How-to Guides and as a result
differs in content and style.

We have adapted the How-to guide from the previous challenge into
the tutorial below. How does the content and language of the tutorial
differ from the how-to guide?



### Tutorial: Changing the File Path for the Spacewalks Output Dataset

#### Introduction
In this tutorial, we will learn how to change the file path for the output dataset generated by Spacewalk.
By the end of this tutorial, you will be able to specify a custom file path for the cleaned dataset.

#### Prerequisites
Before you start, ensure you have the following:

+ Python installed on your system
+ The Spacewalk script (eva_analysis.py)
+ An input dataset (eva-data.json)

####  Prepare the Destination Directory
First, let us decide where we want to save the cleaned dataset.
and make sure the directory exists.

For this tutorial, we will use data/clean as the destination folder.

Let's create the directory if it doesn't exist:

```bash
mkdir -p data/clean
```

#### Run the Spacewalk Script with Custom Path
Next, execute the Spacewalk script and specify the custom file path for the output dataset:
```bash
python eva_analysis.py <input-file> <output-file>
```

Replace <input-file> with your input dataset (eva-data.json) and <output-file> with your desired output path (data/clean/eva-data-clean.csv).

Here is the complete command:
```bash
python eva_analysis.py eva-data.json data/clean/eva-data-clean.csv
```

Notice how the output to the command line clearly indicates that we are using a custom output file path.

```output
TODO
```

After running the script, let us check  the data/clean directory to ensure the
cleaned dataset has been saved correctly.

```bash
ls data/clean
```
You should see eva-data-clean.csv listed in the data/clean folder


#### Exercise: Custom Output Path

+ Create a new directory named output/data in your working directory.
+ Run the Spacewalk script to save the cleaned dataset in the newly created output/data directory with the filename cleaned-eva-data.csv.
+ Verify that the dataset has been saved correctly.

##### Solution

```bash
# Create the directory:
mkdir -p output/data

# Run the script:
python spacewalks.py eva-data.json output/data/cleaned-eva-data.csv

# Verify the output:
ls output/data

# You should see cleaned-eva-data.csv listed
```

### Summary
Congratulations! You have successfully changed the file path for Spacewalks output dataset
and completed an exercise to practice the process. You can now customize the output location
and filename according to your needs.



## Episode: Open project collaboration & management

### Exercise: 
### License selection exercise

Q: You have created a library of functions that are commonly used by
researchers in your field. You would like to share this code with your
research community and ensure that the code remains as open as possible
to benefit the community. But you would also like to see it being
integrated into as many different research codes and even commercial
products as possible. What would be a good choice of license? (hint: You
can use the [choosealicense.com](https://choosealicense.com) website to help you)


### Exercise: 
### License selection exercise 2

Choose a license for your code and data from the pervious exercises.
Discuss with your neighbour or the group your choice of license and
reason for choosing it.


### Exercise: 
### Adding a license to your code

Add a LICENSE file containing the full text of the license you've chosen to the Git repository of your code from 
previous chapters of this lesson.
Add a copyright statement, the name of the license you are using and a
mention of the LICENSE file to at least one source file  
Push your changes to your Github repository. Check the "About" section of your repository's Github webpage and see 
if there is now a license listed.


### Exercise: 
### Relicensing exercise

Q: Find the webpage of a major open source project that is relevant to
your research or the `Spacewalks` codebase we have been working with. See if you can find a contributor license agreement. Add a
link to this in the chat/etherpad/hackmd. 

Hint: try looking at Matplotlib - https://matplotlib.org which Spacewalks uses for plotting


### Exercise: 
### Archive your repository to Zenodo

 * Create an account on Zenodo that is linked to your Github account.
 * Use Zenodo to create a release for your repository and obtain a DOI for it.
 * Get the link to the DOI badge for your repository and add a link to this image to your README file in 
Markdown format. Check that this is the DOI for the latest version and not the DOI for a specific version, 
if not you'll be updating this every time you make a release.

## Episode: "My Research Software"

### Exercise: 
### Add a citation file to your repository

Create a CITATION.cff file for your code and add it to your Github repository. Be sure to include the DOI you were allocated earlier on.


### Exercise: 
### Write an issue to describe our bug

Create a new issue in your repository's issue tracker by doing the following:

 - Go to the Github webpage for your code
 - Click on the Issues tab
 - Click on the "New issue" button
 - Enter a title and description for the issue
 - Click the "Submit Issue" button to create the issue.



### Exercise: 
### Pull Request Exercise

Q: Work in pairs for this exercise. Share the Github link of your repository with your partner. 
If you have set your repository to private, you'll need to add them as a collaborator. Go to the settings page on your Github repository's webpage, click on Collaborators from 
the left hand menu and then click the green "Add People" button and enter the Github username or email address of your partner. 
They will get an email and an alert within Github to accept your invitation to work on this repository, without doing this they won't be able to access it.

 - Now make a fork of your partners repository. 
 - Edit the CITATION.cff file and add your name to it.
 - Commit these changes to your fork
 - Create a pull request back to the original repository
 - Your partner will now receive your pull request and can review 

## Episode: Ethical considerations for research software

### Exercise: 
Good research software practices apply not only when we develop software ourselves, but also when we reuse other 
people's software. Discuss as group and write down in the shared document your thoughts about what ethical 
considerations should we have in mind and pros and cons we should weigh in when choosing other people's software for 
reuse.


### Exercise: 
The licensing and intellectual property (IP) of code generated by large language models (LLMs) and 
[AI pair programmers](https://www.codium.ai/glossary/pair-programming/#:~:text=Ethics%20in%20AI%20Pair%20Programming) 
(such as [CodeGen](https://www.codegen.com/) or [Google Copilot](https://github.com/features/copilot)
which operate with an AI system as one of the code developers) raise complex legal and ethical questions that are not 
clear cut. 
Discuss as group and write down in the shared document some considerations and pros and cons of using AI-generated code.


### Exercise: 
You have been tasked with writing software to scrape a public forum to collect personal data for your study - 
discuss as a group and write down what ethical issues should you consider and how should you act in this case?


### Exercise: 
Often our research software is written for use on HPC systems. 
Discuss as a group and write down in which way can we improve our practices when writing, testing and running code 
on HPC system to support more responsible and less wasteful use of resources.

## Episode: Wrap-up
