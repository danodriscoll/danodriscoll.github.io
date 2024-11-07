# Test

Some Python code.

```python
import numpy as np

def income_group(person_income, average_income):
    if person_income > average_income * 1.2:
        return "high"
    elif person_income < average_income * 0.8:
        return "low"
    else:
        return "middle"
```
