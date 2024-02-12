+++
title = 'Taxation Themes'
date = 2024-02-12T07:08:17Z
draft = true
toc = true
tags = [
    "parameters",
]
categories = [
    "model",
]
series = [""]
+++
A summary of model taxation schemes offered.
<!--more-->

The model develops three taxation schemes for removing household agent wage and interest income. The flat and marginal rate schemes will remove a percentage or arrangement of percentages of income received by every household agent. The third scheme, a draft, removes a specific percentage of income received by amount **and** agent class *type*.

## Flat Rate Taxation

{{< highlight python >}}
def flatTaxToPay(self, amount, rate):
    """ Flat rate tax to pay. """
    flat_tax_to_pay = Decimal('0.000')
    flat_tax_to_pay = amount * zero_division(rate, 100)

    return flat_tax_to_pay
{{< /highlight >}}

## Marginal Rate Taxation

{{< highlight python >}}
def marginalTaxToPay(self):
    """
    Bracket 0: No tax on any wage upto the first 50% of the average wage amount.
    Bracket 1: Pay 60% tax on any remaining wage amount that is between 50% and 100% of the average wage amount.
    Bracket 2: Pay 70% tax on any remaining wage amount that exceeds 100% of the average wage amount.
    """
    marginal_tax_to_pay = 0

    bracket_one_amount = 0
    bracket_two_amount = 0

    if self._wage <= Household.average_wage:
        bracket_one_amount = self._wage - (Household.average_wage * 0.5)
    else:
        bracket_one_amount = Household.average_wage * 0.5
        bracket_two_amount = self._wage - Household.average_wage

    if self._wage > 0:
        marginal_tax_to_pay = (bracket_one_amount * 0.6) + (bracket_two_amount * 0.7)

    return marginal_tax_to_pay
{{< /highlight >}}

## Taxation by Household Agent Type (Draft)

This draft describes how employment and taxation might apply to household agents by class type.

**Households: A Class of Model Agents**

Household agents have attributes which, among others, include *equity* and *type*. In every step, a household agent will note its accumulated equity (wealth). It will also belong to one of three *type* divisions; alpha, beta and gamma. To which division an agent belongs (at every step) will depend on its wealth that is some percentage greater or less than the average wealth of all household agents in the current step.

Producer agents receive an equal share of government expenditure at the beginning of every step. Household agents are available for employment. Each producer will choose to employ (by random choice) an unemployed alpha household agent seventy-five percent of the time. Failing to find an unemployed alpha, a beta agent is sought. If all beta agents are employed, gamma agents are sought by producers still looking to employ. System unemployment (in every step) is inevitable when the number of household agents exceeds the number of producer agents.

**Applicable Taxation Liability Percentage by Agent Type**

Government taxation rates apply by household agent *type*: alpha, 25%; beta, 35%; gamma, 45%.

**Wealth and the Perception of Taxation**

Household agents think about their wealth. To assist thinking, households discuss their wealth with other agents. Though it may only communicate with another of the same type, a household has no preference for which other agent it will contact. Agents communicate on a random choice basis. A feature to note about household discussions of wealth: When contacted, there is a ten percent chance the agent spoken to will inform that its wealth is between 1% and 5% greater than the actuality. A five percent chance it will say it is between 1% and 5% less wealthy. Households will accurately state their wealth, on average, eighty-five percent of the time.

**Agent wealth and mutually exclusive possibilities a household agent will advocate for lower taxation**

| Wealth in Current Step | Alpha Agent | Beta Agent | Gamma Agent |
| ---------------------  | ----------- | ---------- | ----------- |
| *IF > Own Previous Step Wealth* | 80 to 85% of time | 70 to 75% of time | 60 to 65% of time |
| *IF >= Other Agent Wealth* | 86 to 95% of time | 76 to 85% of time | 66 to 75% of time |
| *IF < Other Agent Wealth by 5%* | 96 to 100% of time | 86 to 95% of time | 76 to 85% of time |

