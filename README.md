# Purpose
Test out the Fermat's little theorem on prime numbers.

# Results
Composite numbers less than 1000 with the highest fraction of values that have:
```
((n ** (p - 1)) %p == 1
```

true:
```
[(0.5704099821746881, 561, 320),
 (0.46088193456614507, 703, 324),
 (0.3956043956043956, 91, 36),
 (0.2993762993762994, 481, 144),
 (0.2932551319648094, 341, 100),
 (0.2706766917293233, 133, 36),
 (0.26666666666666666, 15, 4),
 (0.25, 4, 1),
 (0.24615384615384617, 65, 16),
 (0.2222222222222222, 9, 2)]
```

# How many samples to ensure 1 in a million error?
Assume the worst case: we are testing 561for primality. It has a 57.04% of being a Fermat's witness for any sample `n`.

Assuming independent samples:
```
0.5704 ** x < 1e-6
x ln(0.5704) < -6 ln(10)
x < -6 ln(10) / ln(0.5704)
```

Python says:
```
>>> from math import log
>>> -6 * log(10) / log(0.5704)
24.608268847356907
```

So if I have the math right, you need to take 25 samples in the worst case to have a 1 in 1 million chance of a false positive (with no false negatives).

# Comments
Interesting how these factors recur:
- 11: 341 (11 * 31), 561 (3 * 11 * 17)
- 13: 91 (13 * 7), 65 (5 * 13), 481 (13 * 37)
- 37: 703 (19 * 37), 481 (13 * 37)
