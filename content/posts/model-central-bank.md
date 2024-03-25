+++
title = 'Model Central Bank'
date = 2024-02-29T06:07:44Z
draft = false
toc = false
tags = [
    "development",
]
categories = [
    "model",
]
series = [""]
+++
This is a simple Central Bank agent. The model consumes a time-series of historic UK interest (base) rates. (See [Resource]({{< ref "/resource" >}} "Model Input: Real-World Interest Rates")).
<!--more-->

{{< highlight python >}}
class CentralBank(Agent):
    """A Central Bank Agent"""
    def __init__(self, rate_data, unique_id, model) -> None:
        self.breed = "Central Bank"
        self.period = 0 # Model run step.

        # Central bank base rates.
        self.rate_data = rate_data # Importing the rates dataframe into the class.

        # Current accounts
        self.INTcb = 0 # Interest received on government bills held.
        self.Fcb = 0 # Central bank profits to distribute to government.

        # Capital accounts
        self.Bcbd = 0 # Government bills held. A residual, after household bill demands.
        self.Hs = 0 # High-powered money supplied to households.
        self.Hs_Last = 0 # High-powered money supplied to households in the previous step.


    def step(self):
        """
        1 Set the rate of interest on bills.
        2 Distribute profit on Government bills back to the Government. (t-1)
        3 Purchase government bills surplus to household requirements. (t)
        """
        #1
        self.rb = float(rate_data['value'].iloc[self.period]) # Historic rates.

        """
        Beyond historic rates:
        Get all bills 'velocity' and 'acceleration' recordings for policy rate function.
        """
        # self.rb = policy_interest_rate(
        #   redis.lrange("bills:velocity", 0, -1),
        #   redis.lrange("bills:acceleration", 0, -1),
        #   self.period
        #   )

        #2
        government = get_agents_of_type("Government") # Communicate with Government Agent.
        self.Fcb = self.INTcb # Interest received from government.
        government.Fcb += self.Fcb # Distribute profit to government.

        #3
        """
        (Equation 5.15) ΔHs ≡ Hs - Hs₋₁ = ΔBcb

        The amount of cash money supplied by the central bank is simply equal to the
        amount of bills purchased by the central bank.
        """
        self.Bcbd = self.Hs - self.Hs_Last
        government.Bcbs = self.Bcbd

        # Complete Central Bank actions in this step.
        self.period += 1
{{< /highlight >}}

