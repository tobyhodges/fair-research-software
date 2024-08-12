---
title: Code structure
teaching: 60
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions

- ...

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
After completing this episode, participants should be able to:

- ...

::::::::::::::::::::::::::::::::::::::::::::::::

A placeholder for code structure episode. 

- Carry on about functions - add a section on `__main__`
- Directory structure of our code - data folder, code folder, tests folder, documentation folder
- command line interface

Code structure also helps with code readability - but also following the code structure conventions makes it easier to switch 
to another programming language.

## Carry on about functions - improve the rest of our code

Finally, let's apply these good practices to `eva_data_analysis.py`
and organise our code into functions with descriptive names and docstrings.

``` python
import pandas as pd
import matplotlib.pyplot as plt
import sys


def read_json_to_dataframe(input_file_):
    """
    Read the data from a JSON file into a Pandas dataframe.
    Clean the data by removing any incomplete rows and sort by date

    Args:
        input_file_ (str): The path to the JSON file.

    Returns:
         eva_df (pd.DataFrame): The loaded dataframe.
    """
    print(f'Reading JSON file {input_file_}')
    eva_df = pd.read_json(input_file_, convert_dates=['date'])
    eva_df['eva'] = eva_df['eva'].astype(float)
    eva_df.dropna(axis=0, inplace=True)
    eva_df.sort_values('date', inplace=True)
    return eva_df


def write_dataframe_to_csv(df_, output_file_):
    """
    Write the dataframe to a CSV file.

    Args:
        df_ (pd.DataFrame): The input dataframe.
        output_file_ (str): The path to the output CSV file.

    Returns:
        None
    """
    print(f'Saving to CSV file {output_file_}')
    df_.to_csv(output_file_, index=False)

def text_to_duration(duration):
    """
    Convert a text format duration "HH:MM" to duration in hours

    Args:
        duration (str): The text format duration

    Returns:
        duration_hours (float): The duration in hours
    """
    hours, minutes = duration.split(":")
    duration_hours = int(hours) + int(minutes)/60
    return duration_hours


def add_duration_hours_variable(df_):
    """
    Add duration in hours (duration_hours) variable to the dataset

    Args:
        df_ (pd.DataFrame): The input dataframe.

    Returns:
        df_copy (pd.DataFrame): A copy of df_ with the new duration_hours variable added
    """
    df_copy = df_.copy()
    df_copy["duration_hours"] = df_copy["duration"].apply(
        text_to_duration
    )
    return df_copy


def plot_cumulative_time_in_space(df_, graph_file_):
    """
    Plot the cumulative time spent in space over years

    Convert the duration column from strings to number of hours
    Calculate cumulative sum of durations
    Generate a plot of cumulative time spent in space over years and
    save it to the specified location

    Args:
        df_ (pd.DataFrame): The input dataframe.
        graph_file_ (str): The path to the output graph file.

    Returns:
        None
    """
    print(f'Plotting cumulative spacewalk duration and saving to {graph_file_}')
    df_ = add_duration_hours_variable(df_)
    df_['cumulative_time'] = df_['duration_hours'].cumsum()
    plt.plot(df_.date, df_.cumulative_time, 'ko-')
    plt.xlabel('Year')
    plt.ylabel('Total time spent in space to date (hours)')
    plt.tight_layout()
    plt.savefig(graph_file_)
    plt.show()


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

    write_dataframe_to_csv(eva_data, output_file)

    plot_cumulative_time_in_space(eva_data, graph_file)

    print("--END--")

```

Finally, let's commit these changes to our local repository and then push to our remote repository on GitHub to publish
these changes.
Remember to use an informative commit message.

```bash
git status
git add eva_data_analysis.py
git commit -m "Organise code into functions"
git push origin main
```



## Command-line interface to code

Let's add a command-line interface to our script to allow us pass the data file to be read and the output file to be
written to as parameters to our script and avoid hard-coding them.
This improves interoperability and reusability of our code as it can now be run from the
command line terminal and integrated into other scripts or workflows/pipelines (e.g. another script can produce our
input data and can be "chained" with our code in a data analysis pipeline).

We will use `sys.argv` library to read the command line arguments passes to our script and make them available in our
code as a list.
The first element of the list is the name of the script itself, and the following
elements are the arguments passed to the script.

Our modified code will now look as follows.

```python
import pandas as pd
import matplotlib.pyplot as plt
import sys


if __name__ == '__main__':

    if len(sys.argv) < 3:
        data_f = './eva-data.json'
        data_t = './eva-data.csv'
        print(f'Using default input and output filenames')
    else:
        data_f = sys.argv[1]
        data_t = sys.argv[2]
        print('Using custom input and output filenames')

    g_file = './cumulative_eva_graph.png'

    print(f'Reading JSON file {data_f}')
    data = pd.read_json(data_f, convert_dates=['date'])
    data['eva'] = data['eva'].astype(float)
    data.dropna(axis=0, inplace=True)
    data.sort_values('date', inplace=True)

    print(f'Saving to CSV file {data_t}')
    data.to_csv(data_t, index=False)

    print(f'Plotting cumulative spacewalk duration and saving to {g_file}')
    data['duration_hours'] = data['duration'].str.split(":").apply(lambda x: int(x[0]) + int(x[1])/60)
    data['cumulative_time'] = data['duration_hours'].cumsum()
    plt.plot(data.date, data.cumulative_time, 'ko-')
    plt.xlabel('Year')
    plt.ylabel('Total time spent in space to date (hours)')
    plt.tight_layout()
    plt.savefig(g_file)
    plt.show()
    print("--END--")
```

We can now run our script from the command line passing the json input data file and csv output data file as:

```bash
python eva_data_analysis.py eva_data.json eva_data.csv
```

Remember to commit our changes.

```bash
git status
git add eva_data_analysis.py
git commit -m "Add commandline functionality to script"
```
```output
[main b5883f6] Add commandline functionality to script
 1 file changed, 30 insertions(+), 16 deletions(-)
```
