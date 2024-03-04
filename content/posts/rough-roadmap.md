+++
title = 'A Rough Roadmap'
date = 2024-02-17T06:55:36Z
draft = false
toc = true
tags = [
    "development",
]
categories = [
    "model",
    "analysis",
]
series = [""]
+++
Some thoughts on model development.
<!--more-->

## Model

The model consumes real-world UK economic time-series data ranging from Q1 1974 to the latest available. Model development seeks to enhance agent decision-making that is required to go *beyond* the latest available time-series. Specifically, the logic of government, central bank, and household(s) with respect to *expenditures*, *interest rate* policy and *asset portfolio* decisions respectively.

### Agent Logic & Accounting

- Government:
    - Pure expenditures percentage increase is a quantitative response to the trend direction of (model) consol yield. See ‘The Treasury view’: Godley & Lavoie, chapter 5, pp 147-165.
- Central Bank:
    - The interest (base) rate set is a reaction to (model) monetary system velocity; one part of the decision-tree analysis also informed by real-world BoE interest rate decisions.
    - *Forward Guidance:* Interest rate in the next step:
        - Rate decisions made public are accurately stated 50% of the time (on average) to *non-preferred* household agents.
        - Rate decisions made available to *preferred* household agents are accurate 100% of the time.
    - Account for long-term bonds (consol account) on the asset side of the Central Bank balance sheet.
- Producer(s):
    - May employ multiple household agents.
- Household(s):
    - Have bond price expectations reflecting Central Bank forward guidance.

## Time-Series Data

### From Quarterly to Monthly Time-Series

The expenditure data consumed by the model is a quarterly financial series. Both model and output analysis may benefit from *exploding* the quarterly series into a monthly series before model consumption. A monthly time series of interest (base) rates is offered by the Central Bank (See [Resource]({{< ref "/resource" >}} "Time Series Resource")).

### Quarterly Expenditure to Monthly Series: Draft Notebook Script

{{< notebook "jupyter/monthly_expenditure_example" 1600 >}}
