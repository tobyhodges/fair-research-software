## Episode: "Course introduction"
## Episode: "FAIR research software"

Think of a piece of software you use in your research - any computational tool used for data gathering, modelling & simulation, processing & visualising results or others. 
If you have a bit of code or software you wrote yourself, in any language, feel free to use that.

Think where on the FAIR spectrum it fits, using the following scale as a guide for each principle:

- 1 - requires loads of improvement
- 2 - on a good path, but improvements still needed
- 3 - decent, a few things could still be improved
- 4 - very good, only tiny things to improve upon
- 5 - excellent

## Episode: "Tools and practices for research software development"

Run the following commands in a Bash shell to check you have installed the tools listed in the Setup page. Compare the output with your neightbour and see if you can see any differences.

1. `echo $SHELL`
2. `pwd`
3. `whoami`
4. `python --version`
5. `which python`
6. `git --help`
7. `code`

## Episode: Version control

### Add and commit the changed file

Using the Git commands demonstrated so far, save the change you just made to the Python script.

Remember, commit messages should be descriptive and complete the sentence "If applied, this commit will...".
You can also use `git status` to check the status of your project at any time.


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


### Understanding commit contents

Below are the `diff`s of two commits. A `diff` shows the differences in a file (or files!) compared to the previous 
commit in the history so you can what has changed. 
The lines that begin with `+`s represent additions, and the lines that begin with `-`s represent deletions. 
Compare these two commit `diff`s. 
Can you understand what the commit author was trying to achieve in each commit? 
How many changes have they tried to make in each commit? 
Discuss in pairs or small groups.

1. ![Example Diff 1](fig/ex-diff-1.png)
2. ![Example Diff 2](fig/ex-diff-2.png)


### Terminology

In pairs or small groups, discuss the difference between the terms `remote`
and `origin`. What is the definition of each term?

## Episode: Code readability

### Give a descriptive name to a variable

Below we have a variable called `var` being set the value of 9.81.
`var` is not a very descriptive name here as it doesn't tell us what 9.81 means, yet it is a very common constant in physics!
Go online and find out which constant 9.81 relates to and suggest a new name for this variable.

Hint: the units are _metres per second squared_!

```python
var = 9.81
```


### Add some comments to a code block

Examine lines 7 to 20 of the `bad-code.py` script.
Add (or change!) as many inline comments as you think is required to help yourself and others understand what that code block is doing.

Hint: Inline comments in Python are denoted by a `#` symbol.


### Create a function

Below is a function that reads in a JSON file into a dataframe structure using the [`pandas` library](https://pandas.pydata.org/) - but the code is out of order!
Reorder the lines of code within the function so that the JSON file is read in using the `read_json` method, any incomplete rows are _dropped_, the values are _sorted_ by date, and then the cleaned dataframe is _returned_.
There is also a `print` statement that will display which file is being read in on the command line for verification.

```python
import pandas as pd

def read_json_to_dataframe(input_file):
    eva_df.sort_values('date', inplace=True)
    eva_df.dropna(axis=0, inplace=True)
    print(f'Reading JSON file {input_file}')
    return eva_df
    eva_df = pd.read_json(input_file, convert_dates=['date'])
```


### Writing docstrings

Write a docstring for the `read_json_to_dataframe` function from the previous
exercise. Things you may want to consider when writing your docstring are:

- Describing what the function does
- What kind of inputs does the function take?
  Are they required or optional?
  Do they have default values?
- What output will the function produce?

Hint: Python docstrings are defined by enclosing the text with `"""` above and
below. This text is also indented to the same level as the code defined beneath
it, which is 4 whitespaces.

## Episode: "Code testing"

## Types of Software Tests

Fill in the blanks in the sentences below:

+ __________ tests compare the ______ output of a program to its ________ output
  to demonstrate correctness.
+ Unit tests compare the actual output of a ______ ________ to the expected output
  to demonstrate correctness.
+ __________ tests check that results have not changed since the previous test run.
+ __________ tests check that two or more parts of a program are working together correctly.


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


## Write Unit Tests

Implement unit tests for the `calculate_crew_size` function. 
Cover typical cases and edge cases.


## Evaluate Code Coverage

Generate a code coverage report for the `Spacewalks` test suite
and extract the following information:

a.  What proportion of the code base is currently NOT exercised by the test suite?
b.	Which functions in our code base are currently untested?


## Implementing a minimal test suite

A member of our research team shares the following code
with us to add to the Spacewalks codebase:

```python
def summarise_categorical(df_, varname_):
    """
    Tabulate the distribution of a categorical variable

    Args:
        df_ (pd.DataFrame): The input dataframe.
        varname_ (str): The name of the variable

    Returns:
        pd.DataFrame: dataframe containing the count and percentage of
        each unique value of varname_
        
    Examples:
        >>> df_example  = pd.DataFrame({
            'vehicle': ['Apollo 16', 'Apollo 17', 'Apollo 17'],
            }, index=[0, 1, 2)
        >>> summarise_categorical(df_example, "vehicle")
        Tabulating distribution of categorical variable vehicle
             vehicle  count  percentage
        0  Apollo 16      1        33.0
        1  Apollo 17      2        67.0
    """
    print(f'Tabulating distribution of categorical variable {varname_}')

    # Prepare statistical summary
    count_variable = df_[[varname_]].copy()
    count_summary = count_variable.value_counts()
    percentage_summary = round(count_summary / count_variable.size, 2) * 100

    # Combine results into a summary data frame
    df_summary = pd.concat([count_summary, percentage_summary], axis=1)
    df_summary.columns = ['count', 'percentage']
    df_summary.sort_index(inplace=True)


    df_summary = df_summary.reset_index()
    return df_summary
```

This looks like a useful tool for creating summary statistics tables, so
let's write a minimal test suite to check that this code is behaving as expected. 

### Challenge 1 - Typical Inputs

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

## Episode: Documenting code

## Spacewalks README

Extend the README for Spacewalks by adding
a. Installation instructions
b. A simple usage example

## Episode: My Software
## Episode: Spacetravel

## `Spacewalks` Software Citation

Write a software citation file for the Spacewalks code and add it to the root
folder of our project.

+ Add the URL of the code repository as a "Related Resources"
+ Add a one-line description of the code under the "Abstract" section
+ Add at least two key words under the "Keywords" section
+ Use the commit hash of your most recent commit to indicate the code
  version your citation file refers to.

## Episode: Spacewalks

## A `Spacewalks` How-to Guide

a. Review the Diataxis guidance page on writing a How-to guide. Identify
three features of an effective how-to guide.

b. Following the Diataxis guidelines, add a How-to Guide to the `docs` folder
that show users how to change the destination filename for the output dataset generated
by Spacewalks.

## Episode: Open project collaboration & management

## License selection exercise

Q: You have created a library of functions that are commonly used by
researchers in your field. You would like to share this code with your
research community and ensure that the code remains as open as possible
to benefit the community. But you would also like to see it being
integrated into as many different research codes and even commercial
products as possible. What would be a good choice of license? (hint: You
can use the [choosealicense.com](https://choosealicense.com) website to help you)


## License selection exercise 2

Choose a license for your code and data from the pervious exercises.
Discuss with your neighbour or the group your choice of license and
reason for choosing it.


## Adding a license to your code

Add a LICENSE file containing the full text of the license you've chosen to the Git repository of your code from 
previous chapters of this lesson.
Add a copyright statement, the name of the license you are using and a
mention of the LICENSE file to at least one source file  
Push your changes to your Github repository. Check the "About" section of your repository's Github webpage and see 
if there is now a license listed.


## Relicensing exercise

Q: Find the webpage of a major open source project that is relevant to
your research. See if you can find a contributor license agreement. Add a
link to this in the chat/etherpad/hackmd. 


## Archive your repository to Zenodo

 * Create an account on Zenodo that is linked to your Github account.
 * Use Zenodo to create a release for your repository and obtain a DOI for it.
 * Get the link to the DOI badge for your repository and add a link to this image to your README file in 
Markdown format. Check that this is the DOI for the latest version and not the DOI for a specific version, 
if not you'll be updating this every time you make a release.

## Episode: "My Research Software"

## Add a citation file to your repository

Create a CITATION.cff file for your code and add it to your Github repository. Be sure to include the DOI you were allocated earlier on.


## Write an issue to describe our bug

Create a new issue in your repository's issue tracker by doing the following:

 - Go to the Github webpage for your code
 - Click on the Issues tab
 - Click on the "New issue" button
 - Enter a title and description for the issue
 - Click the "Submit Issue" button to create the issue.



## Pull Request Exercise

Q: Work in pairs for this exercise. Share the Github link of your repository with your partner. 
If you have set your repository to private, you'll need to add them as a collaborator. Go to the settings page on your Github repository's webpage, click on Collaborators from 
the left hand menu and then click the green "Add People" button and enter the Github username or email address of your partner. 
They will get an email and an alert within Github to accept your invitation to work on this repository, without doing this they won't be able to access it.

 - Now make a fork of your partners repository. 
 - Edit the authors or citation file and add your name to it.
 - Commit these changes to your fork
 - Create a pull request back to the original repository
 - Your partner will now receive your pull request and can review 

## Episode: Ethical considerations for research software

### Which of the following statements are true and which are false?

1. I don’t need permission because I am only using the copyrighted work in educational or non-profit purposes.
2. I should always know the licence of any code, data, libraries, pictures or other work that you reuse or redistribute.
3. Since I’m planning to give credit to the authors who created the work I reuse, I do not have to worry about or need
   permission.
4. Material I obtain from the Internet is publicly accessible so no explicit permission is required.
5. The work I want to use does not have a copyright notice on it, so it’s not protected by copyright and I am free to
   use it.

## Episode: Wrap-up
## Episode: "Using Markdown"

## Challenge 1: Can you do it?

What is the output of this command?

```r
paste("This", "new", "lesson", "looks", "good")
```

