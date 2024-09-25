---
title: Implementing a minimal test suite
teaching: 0
exercises: 30
---

::::::::::::::::::::::::::::::::::::: objectives
After completing this episode, participants should be able to:

- Implement a minimal test suite


::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::: questions

- How can we implement a minimal test suite when someone adds new code to our project?

::::::::::::::::::::::::::::::::::::::::::::::::

### Implementing a minimal test suite

A member of our research team shares the following code with us to add to our existing codebase:

``` python
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
let's integrate this into our `eva_data_analysis.py`code and then write
a minimal test suite to check that this code is behaving as expected.

``` python
import pandas as pd
import matplotlib.pyplot as plt
import sys
import re


...

def add_crew_size_variable(df_):
    """
    Add crew size (crew_size) variable to the dataset

    Args:
        df_ (pd.DataFrame): The input dataframe.

    Returns:
        pd.DataFrame: A copy of df_ with the new crew_size variable added
    """
    print('Adding crew size variable (crew_size) to dataset')
    df_copy = df_.copy()
    df_copy["crew_size"] = df_copy["crew"].apply(
        calculate_crew_size
    )
    return df_copy


def summarise_categorical(df_, varname_):
    """
    Tabulate the distribution of a categorical variable

    Args:
        df_ (pd.DataFrame): The input dataframe.
        varname_ (str): The name of the variable

    Returns:
        pd.DataFrame: dataframe containing the count and percentage of
        each unique value of varname_
    """
    print(f'Tabulating distribution of categorical variable {varname_}')

    # Prepare statistical summary
    count_variable = df_[[varname_]].copy()
    count_summary = count_variable.value_counts() # There is a bug here that we will fix later!
    percentage_summary = round(count_summary / count_variable.size, 2) * 100

    # Combine results into a summary data frame
    df_summary = pd.concat([count_summary, percentage_summary], axis=1)
    df_summary.columns = ['count', 'percentage']
    df_summary.sort_index(inplace=True)


    df_summary = df_summary.reset_index()
    return df_summary


if __name__ == '__main__':

    if len(sys.argv) < 3:
        input_file = './eva-data.json'
        output_file = './eva-data.csv'
        print(f'Using default input and output filenames')
    else:
        input_file = sys.argv[1]
        output_file = sys.argv[2]
        print('Using custom input and output filenames')

    graph_file = './cumulative_eva_graph.png'

    eva_data = read_json_to_dataframe(input_file)

    eva_data_prepared = add_crew_size_variable(eva_data)

    write_dataframe_to_csv(eva_data_prepared, output_file)

    table_crew_size = summarise_categorical(eva_data_prepared, "crew_size")

    write_dataframe_to_csv(table_crew_size, "./table_crew_size.csv")

    plot_cumulative_time_in_space(eva_data_prepared, graph_file)

    print("--END--")
```

To write tests for this function, we'll need to be able to compare
dataframes. The pandas.testing module in the pandas library provides
functions and utilities for testing pandas objects and includes a
function `assert_frame_equal` that we can use to compare two dataframes.

::: challenge
### Exercise 1 - Typical Inputs

First, check that the function behaves as expected with typical input
values. Fill in the gaps in the skeleton test below:

``` python
import pandas.testing as pdt

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

::: solution
``` python
import pandas.testing as pdt

def test_summarise_categorical():
    """
    Test that summarise_categorical correctly tabulates
    distribution of values (counts, percentages) for a simple ground truth
    example
    """
    test_input = pd.DataFrame({
        'country': ['USA', 'USA', 'USA', "Russia", "Russia"],
    }, index=[0, 1, 2, 3, 4])

    expected_result = pd.DataFrame({
        'country': ["Russia", "USA"],
        'count': [2, 3],
        'percentage': [40.0, 60.0],
    }, index=[0, 1])

    actual_result = summarise_categorical(test_input, "country")

    pdt.assert_frame_equal(actual_result, expected_result)
```
:::
:::

::: challenge
### Exercise 2 - Edge Cases

Now let's check that the function behaves as expected with edge cases.\
Does the code behave as expected when the column of interest contains
one or more missing values (pd.NA)? (write a new test).

Fill in the gaps in the skeleton test below:

``` python
import pandas.testing as pdt

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

::: solution
``` python
import pandas.testing as pdt

def test_summarise_categorical_missvals():
    """
    Test that summarise_categorical correctly tabulates
    distribution of values (counts, percentages) for a ground truth
    example (edge case where column contains missing values)
    """
    test_input = pd.DataFrame({
        'country': ['USA', 'USA', 'USA', "Russia", pd.NA],
    }, index=[0, 1, 2, 3, 4])

    expected_result = pd.DataFrame({
        'country': ["Russia", "USA", np.nan], # np.nan because pd.NA is cast to np.nan
        'count': [1, 3, 1],
        'percentage': [20.0, 60.0, 20.0],
    }, index=[0, 1, 2])
    actual_result = summarise_categorical(test_input, "country")

    pdt.assert_frame_equal(actual_result, expected_result)
```
:::
:::

::: challenge
### Exercise 3 - Invalid inputs

Now write a test to check that the `summarise_categorical` function
raises an appropriate error when asked to tabulate a column that does
not exist in the data frame.

Hint: lookup `pytest.raises` in the pytest documentation.

::: solution
``` python

def test_summarise_categorical_invalid():
    """
    Test that summarise_categorical raises an
    error when a non-existent column is input
    """
    test_input = pd.DataFrame({
        'country': ['USA', 'USA', 'USA', "Russia", "Russia"],
    }, index=[0, 1, 2, 3, 4])

    with pytest.raises(KeyError):
        summarise_categorical(test_input, "vehicle")
```
:::
:::