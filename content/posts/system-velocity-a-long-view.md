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
A simple analysis of a model system juxtaposed alongside real-world UK economic time-series data.
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

### Model Bills

{{< highlight python >}}
"""
G&L p146: Govt Budget Constraint (Bs):
(Equation 5.14) ΔBs ≡ Bs - Bs₋₁ == (G + rb₋₁ * Bs₋₁ + BLs₋₁) - (T + rb₋₁ * Bcb₋₁) - ΔBLs₋₁ * PbL

"The bills 'Bs' that need to be newly issued are equal to government expenditures,
including its interest payments minus the govt revenues - taxes and central bank profits - plus
the value of the newly issued long-term bonds. Needless to say, when there is a government surplus,
or when the government deficit is financed by new issues of long-term bonds,
the change in Treasury bills will be negative and bills will be redeemed."
"""

expenditures = self.Gd + self.INT_Bh + self.INT_Bcb + self.INT_BLh
revenues = self.Td + self.Fcb # Taxes and central bank profits.

self.GD = (expenditures - revenues) - val_new_bonds_issued
self.Bs -= self.GD_Close - self.GD_Open
{{< /highlight >}}

### Velocity Model Bills

{{< highlight python >}}
# Model System Velocity: Change in bills issued, from one period to the next,
# divided by national income.
df["velocity_bills"] = ((abs(df["Bs"] - df["Bs"].shift(1)))
                        / df["national_income"]) * 100
{{< /highlight >}}

{{< load-plotly >}}
{{< plotly json="/plotly/json/kenobi-671-model-run-22-02-2024-analysis" height="500px" >}}

This {{< plotly-full-screen html="plotly/html/kenobi-671-model-run-22-02-2024-analysis" link-text="full screen plot" >}} includes time-series annotations highlighting political administration periods and some key moments for model bills velocity and corresponding real-world gilts.
