+++
title = 'System Velocity: A Long View With Interest'
date = 2024-03-07T12:32:48Z
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
A simple analysis of a model system with interest juxtaposed alongside real-world UK economic time-series data.
<!--more-->

## Model System Velocity & Gilt Yields

### Model Run Parameter Inputs

Advancing the earlier post showing the [simplest collection]({{< ref "/posts/system-velocity-a-long-view" >}}) of model run parameters, we now have one household, one producer **and** interest payments on Government monetary assets.

See GiltEdged [model runs](https://docs.google.com/spreadsheets/d/e/2PACX-1vRjjK62BFLfv9bvJb9JLxP0ko_xFBoTSgA0G23Ks4cwArnmkOcT7ik57SPETeLpCQyXMzJM_RCDplop/pubhtml?gid=1130413788&single=true).

- Run Name: r2d2-477-model-run-22-02-2024
- Government Expenditure: See *Model Input: Real-World Expenditures* from the [resource]({{< ref "/resource" >}} "Time Series Resource") page.
- Taxation rate: 37% (Flat rate; all household agents)
- Coupon Rate: 1%
- Interest Rate: See *Model Input: Real-World Interest Rates* from the [resource]({{< ref "/resource" >}} "Time Series Resource") page.

### Velocity Model Bills

{{< load-plotly >}}
{{< plotly json="/plotly/json/r2d2-477-model-run-22-02-2024-analysis-sys-velocity" height="500px" >}}

### Model Bond Price

{{< plotly json="/plotly/json/r2d2-477-model-run-22-02-2024-analysis-bond-price" height="500px" >}}

### Model Bond Yield

{{< plotly json="/plotly/json/r2d2-477-model-run-22-02-2024-analysis-bond-yield" height="500px" >}}

### Model Interest Payments

{{< plotly json="/plotly/json/r2d2-477-model-run-22-02-2024-analysis-int-payments" height="500px" >}}

### Model Interest & Debt

{{< plotly json="/plotly/json/r2d2-477-model-run-22-02-2024-analysis-int-payments-debt" height="500px" >}}
