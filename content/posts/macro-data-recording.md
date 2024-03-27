+++
title = 'Macro Data Function'
date = 2024-03-25T13:56:43Z
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
A first draft model macro-data recording function. The *velocity* and *acceleration* of the system.
<!--more-->

{{< highlight python >}}
import numpy as np
import redis

r = redis.Redis(decode_responses=True)

# Utility: Catch divide by zero error.
def zero_division(n, d):
    return n / d if d else 0

"""
Used by the Central Bank.
"""

# Called by Government.
def pushBills(val):
    def pushVelocity():
        def pushAcceleration():
            # Calculate acceleration of bills issued.
            vel_bills_arr = np.array(r.lrange("bills:velocity", 0, 1), dtype=float) # Get last two entries.
            acc_bills_arr = np.diff(vel_bills_arr) # The change in velocity.
            r.lpush("bills:acceleration", float(acc_bills_arr))
            return True

        # Calculate velocity of bills issued.
        bills_arr = np.array(r.lrange("bills:issued", 0 ,1), dtype=float) # Get last two entries.
        national_income = float(r.get("national:income"))

        vel_bills = zero_division(abs(float(np.diff(bills_arr))), national_income) * 100
        r.lpush("bills:velocity", float(vel_bills))
        return pushAcceleration()

    # Push new amount of bills issued in this step.
    r.lpush("bills:issued", val)
    return pushVelocity()


# Called by Producer(s).
def addNatIncome(val):
    old_national_income = float(r.get("national:income"))
    new_national_income = old_national_income + float(val)

    r.set("national:income", new_national_income)
    return True
{{< /highlight >}}