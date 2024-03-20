+++
title = 'Model Time Series Input'
date = 2024-03-20T12:57:07Z
draft = false
toc = false
tags = [
    "parameters",
]
categories = [
    "model",
]
series = [""]
+++
Exploding model time-series data input.
<!--more-->

## From Quarterly to Monthly Time-Series

The expenditure data consumed by the model is a quarterly financial series. Both model and output analysis may benefit from *exploding* the quarterly series into a monthly series before model consumption. A monthly time series of interest (base) rates is offered by the Central Bank (See [Resource]({{< ref "/resource" >}} "Time Series Resource")).

### Quarterly Expenditure to Monthly Series: Draft Notebook Script

{{< notebook "jupyter/monthly_expenditure_example" 1600 >}}