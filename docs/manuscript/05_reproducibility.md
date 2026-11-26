# Reproducibility {#sec:reproducibility}

## Recompute the experiment

The objective is a pure function of the parameter vector and seed. The
coordination loop receives a fixed objective, proposer policy, and
configuration. The analysis scripts run that simulation and write the
comparison and ablation JSON plus their three figures.

```sh
uv sync --locked --python 3.13 --extra dev
uv run --no-sync --python 3.13 python scripts/run_search_comparison.py
uv run --no-sync --python 3.13 python scripts/run_ablation.py
```

The repository tracks a published output snapshot. A new run recomputes the
metrics in a disposable checkout. Details such as font rendering can vary
across software environments.

## Verify the core and replay contract

```sh
uv run --no-sync --python 3.13 pytest -q -m 'not requires_ollama' --cov=src --cov-fail-under=90
```

The suite checks the deterministic coordination mechanisms and tests the
published numerical results against fresh computation. The offline transcript
fixture separately exercises schema and revision checks. Replay returns
recorded role and content fields after validation. It does not supply the
proposals used by the comparison or ablation.

The optional Hermes adapter uses a separately served model. Its integration
test is outside the provider-free build and supplies no measurements to this
manuscript.

## Shared estimator

The noise-band confirmation estimator is generic. A synchronized copy lives
at `infrastructure.scientific.confirmation` for reuse by projects comparing
a stochastic metric to a baseline. The testbed carries its standalone copy.
