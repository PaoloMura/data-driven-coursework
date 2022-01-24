# data-driven-coursework

This repository is my solution to the year 2 Data-Driven Computer Science coursework. The task description can be found in `CW1.pdf`, my program solution is `lsr.py` and my report is in `report.pdf`. A summary of the task is as follows.

## The Task

Given a set of training data files in the `datafiles/train_data` directory, use linear regression to learn a model that fits the data. Three functions were used to create the data: a linear function, a polynomial function of unknown order and an unknown function.

## My Solution

I used linear least squares regression to train the model. This used a maximum likelihood equation to find the parameters of the model. In order to reduce overfitting, I used two very similar cross-validation techniques. The first was k-fold cross-validation to determine the order of the polynomial and the type of the unknown function. The second was leave-p-out cross-validation to measure each model's performance and select between them at runtime.

## Result

Visual inspection can easily be used to rate the performance of my solution. My program seems to correctly determine the function in all but one case. For this anomaly, the reason appears to be too small an amount of data with a large amount of noise.

I achieved a mark of 83 in this unit.
  
## How to run
  
### Requirements
* Python3
* Numpy
* Pandas
* Matplotlib

### Command

Use `python lsr.py basic_2.csv` to run the program on the `basic_2.csv` file.

For each consecutive 20 points in the file, it will select between the three functions (linear, order-3 polynomial and sine) using cross-validation. It will then fit this function to the points using linear least squares regression. Finally it outputs the sum-squared error of the fitted line.

Replace the filename to use this program on any of the given training data files.

### Options

The following options can be used with the command above:

`--pi-hunt` searches all files for multiples of π/2 in the x data, returning true if found

`--data=k` plots the raw input data for segment k ≥ 0

`--plot` plots the fitted curve for all segments

`--plot=k` plots the fitted curve for segment k ≥ 0 only

`--func=k` forces the specified function to be used for fitting<sup>1</sup>

`--eval=k` evaluates the performance of all models on segment k ≥ 0

`--analyse` evaluates the performance of all functions across all files and displays a graph summarising the results.

1 - Using 0 ≤ k ≤ 20 will choose a polynomial of order k. Alternatively, k can be one of `sin`, `tan` or `exp` for sine, tangent and exponential functions respectively. Use this option together with `--plot` or `--plot=k`.
