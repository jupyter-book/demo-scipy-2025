---
title: Doing Serious Science
subtitle: A research paper, definitely
kernelspec:
  name: python3
  display_name: Python 3
---

# Doing serious science

Wait, we need data. Numpy is scientific, let's use a numpy.

```{code-cell} python3

import numpy as np
household_spending = np.array([600,657,656,679,715,731,751,756,769,783,837,858,876,977,1033,1099,])
google_searches = np.array([5.58333,5.41667,6.5,6.66667,11.4167,13.5,17.75,22,28,29.4167,43.25,48.6667,53.5833,66.1667,55.25,89.1667,])
```

Graphs are scientific, let's do a graph.

```{code-cell} python3
:label: cell:correlation

from matplotlib import pyplot as plt

fig, ax1 = plt.subplots()
ax1.plot(household_spending, marker='o')
ax1.set_ylabel("Annual household spend")

ax2 = ax1.twinx()
ax2.plot(google_searches, 'C2', marker='o')
ax2.set_ylabel("# Google searches")

ax1.set_xlabel("Year")

ax1.set_title(
    "Annual US household spending on fruits and vegetables \ncorrelates with\nGoogle searches for 'how to learn python'"
);
```

P-values are scientific. Let's win the P-value.

```{code-cell} python3
from scipy import stats

# Calculate Pearson correlation coefficient and p-value
correlation, p_value = stats.pearsonr(household_spending, google_searches)
```

:::{important} P-Value is Significant
The figure shown in @cell:correlation is a super _serious_ bit of science. Look, it has a P-value of {eval}`format(p_value, ".3E")`. It must be real!

The inspiration and data for this plot were taken from [Tyer Vigen].
:::

[Tyer Vigen]: https://www.tylervigen.com/spurious/correlation/19254_annual-us-household-spending-on-fruits-and-vegetables_correlates-with_google-searches-for-how-to-learn-python
