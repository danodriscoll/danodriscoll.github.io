+++
title = 'System Velocity: A Long View'
date = 2024-02-29T07:40:26Z
draft = false
toc = false
tags = [
    "plot",
    "gilt"
]
categories = [
    "model",
    "analysis"
]
series = [""]
+++
A simple analysis of model output juxtaposed alongside real-world UK economic time-series data.
<!--more-->

## Model System Velocity & Gilt Yields: An Opening Data Analysis

### Model Run Parameter Inputs

See GiltEdged [model runs](https://docs.google.com/spreadsheets/d/e/2PACX-1vRjjK62BFLfv9bvJb9JLxP0ko_xFBoTSgA0G23Ks4cwArnmkOcT7ik57SPETeLpCQyXMzJM_RCDplop/pubhtml?gid=1130413788&single=true).

The simplest suite of model run parameters: One, household, one producer and a system free from interest payments on Government monetary assets.

- Run Name: kenobi-671-model-run-22-02-2024
- Government Expenditure: See *Model Input: Real-World Expenditures* from the [resource]({{< ref "/resource" >}} "Time Series Resource") page.
- Taxation rate: 37% (Flat rate; all household agents)
- Coupon Rate: 0%
- Interest Rate: 0%

### Velocity_Bills

{{< highlight python >}}
# Model System Velocity: Change in bills issued, from one period to the next,
# divided by national income.
df["velocity_bills"] = ((abs(df["bills_issued"] - df["bills_issued"].shift(1)))
                        / df["national_income"]) * 100
{{< /highlight >}}

{{< load-plotly >}}
{{< plotly json="/plotly/json/kenobi-671-model-run-22-02-2024-analysis" height="500px" >}}

This {{< plotly-full-screen html="/plotly/html/kenobi-671-model-run-22-02-2024-analysis" link-text="full screen plot" >}} includes time-series annotations highlighting political administration periods and some key moments for model bills velocity and corresponding real-world gilts.
