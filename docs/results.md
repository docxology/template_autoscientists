# Read the testbed results

The [comparison summary](../output/data/search_comparison.json) and
[ablation summary](../output/data/ablation.json) are the tracked release
snapshot. The [offline commands](quickstart.md) compute new results in the
checkout where they run.

| Measure | Result for the shipped objective |
| --- | --- |
| Clean solution quality | Coordinated teams and the one-team baseline reach the same optimum. |
| First reach of the clean optimum | The coordinated run takes 16 experiments, versus 12 for the baseline. |
| Redundant re-probes | The dead-end registry cuts them from 36 to zero. The run then stops after 36 of 60 allotted experiments. |
| Accepted evaluation noise | Removing confirmation increases the reported-vs-clean gap by about thirteenfold. |
| Ranking and reorganization | Each removal leaves the measured quantities unchanged. |

The [comparison plot](../output/figures/search_comparison.png),
[metric ablations](../output/figures/ablation.png), and
[efficiency ablations](../output/figures/ablation_efficiency.png) show
these results. The reported metric comes from seeded evaluations. The clean
metric is the value from the noise-free objective at the champion's parameters.

The comparison uses a shared sequential experiment budget on one synthetic
landscape. It measures behavior under those conditions. Wall-clock parallel
performance and the quality of model-generated proposals require different
experiments.
