+++
title = 'System Acceleration: A Long View'
date = 2024-03-17T08:48:54Z
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
A simple analysis of the acceleration of model bills issued.
<!--more-->

## Model System Acceleration

The earlier post, [system velocity: a long view]({{< ref "/posts/system-velocity-a-long-view" >}} "System Velocity: A Long View"), previewed a model run with the simplest suite of parameter inputs. Extending this simple analysis is a plot showing the acceleration rate of model bills issued.

The earlier post points out two periods, among others, where the velocity of model bills precedes a similar reaction in the real-world Gilt yield. The period between July 1997 and July 2003, however, shows the trend velocity of model bills issued increasing while the trend Gilt yield is decreasing. When looking at the acceleration of model bills issued, we see that across the same period there is actually a negative acceleration trend occurring. The velocity of bills issued may be increasing, but the system is experiencing negative acceleration - to which Gilt yields may be reacting.

{{< highlight python >}}
"""
# Change in the velocity of bills issued, as percentage of national income
# from one period to the next.
"""
import numpy as np

acc_bills = np.diff(df["vel_Bs"])
acc_bills = np.insert(acc_bills, 0, 0) # Insert 0 at the beggining of the acceleration array.
df["acc_Bs"] = acc_bills # Acceleration of bills issued.
{{< /highlight >}}

{{< load-plotly >}}
{{< plotly json="/plotly/json/kenobi-671-model-run-22-02-2024-analysis-sys-acceleration" height="600px" >}}

View the {{< plotly-full-screen html="plotly/html/kenobi-671-model-run-22-02-2024-analysis-sys-acceleration" link-text="full screen plot" >}}.
