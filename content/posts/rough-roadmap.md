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
]
series = [""]
+++
Some thoughts on the direction of model development in early 2024.
<!--more-->

The model consumes real-world UK economic time-series data ranging from Q1 1974 to the latest available. Model development seeks to enhance model agent decision-making that is required to go beyond the latest available time-series. Specifically, the logic of government, central bank, and household(s) with respect to *expenditures*, *interest rate* policy and *asset portfolio* decisions respectively.

## Accounting and Logic Development

**Government Agent**
- Expand government agent logic to include:
    - The effect of household liquidity preference on long rates,
    - Make pure expenditures endogenous in context:
        - A simple bounded [macrofinancial](https://www.data-reports.net/studio-sketch/public-private-finance.html) regime. A macrofinancial regime is a particular combination of monetary, fiscal, and financial institutions, the governance strategy of a state, that shapes the creation and allocation of money.
        - Historical rules; the Treasury view. See Godley & Lavoie, chapter 5, pp 147-165.
    - Distribution, tax and household agent types: View [taxation themes]({{< ref "/posts/taxation-themes" >}} "Government agent taxtion themes").

**Central Bank Agent**
- Expand central bank accounting and logic:
    - Account for long-term bonds on the asset side of the central bank balance sheet.
    - Use historical analysis of interest (base) rate time-series to inform categorical decision-making tree logic.

**Producer and Household Agents**
- Producer agents may employ multiple household agents.
- Household agents as money asset managers: They have bond price expectations; the majority having assumptions about the interest (base) rate in the next step; a minority are attentive to the macro system velocity and momentum.
