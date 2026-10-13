# Part 2: Design Optimization Results

## Solution overview

The simulation models response time as decreasing with the efficiency factor and durability as increasing with the reinforcement factor:

- `new response time = 0.20 s × (1 − efficiency factor)`
- `new durability = 75 × (1 + reinforcement factor)`

To balance both improvements while staying within the design limits, the notebook evaluates all 10,201 pairs of factors from 0.00 to 1.00 in increments of 0.01. A result is considered valid when response time is at least the 0.10-second target and durability does not exceed 100. The combined score adds the percentage reduction in response time to the percentage gain in durability, weighting the two improvements equally.

## Best valid result

| Metric | Baseline | Optimized |
| --- | ---: | ---: |
| Efficiency factor | — | 0.50 (50%) |
| Reinforcement factor | — | 0.33 (33%) |
| Response time | 0.20 s | 0.10 s |
| Durability score | 75.00 | 99.75 |
| Combined improvement score | — | 0.830 |

The sweep found 1,734 valid combinations. The selected factors achieve the response-time target and bring durability close to its 100-point limit without exceeding it. The heatmap shows the score for valid combinations; blank areas are outside the design limits, and the red marker indicates the best-scoring valid pair.

![Heatmap of valid design-factor combinations and the selected optimum](./results/part-2-factor-sweep.png)

## Interpretation

In this simplified model, a 50% efficiency improvement halves response time. A 33% reinforcement factor raises the durability score by 24.75 points. Together, these give a combined score of 0.830 under the notebook's equal-weight scoring rule.

These values are simulation results, not measured hardware performance. The linear relationships and limits are assumptions for the exercise; a real design would need engineering review and physical testing.
