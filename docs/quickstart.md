# Quick start

Install Git, uv, and Python 3.11 or later. The following commands select
Python 3.13, install the locked development environment, and run the
provider-free test suite from the repository root:

```sh
uv sync --locked --python 3.13 --extra dev
uv run --no-sync --python 3.13 pytest -q -m 'not requires_ollama' --cov=src --cov-fail-under=90
```

Run the two analysis scripts in a disposable checkout. Both write to
`output/`, which also holds the tracked publication snapshot.

```sh
uv run --no-sync --python 3.13 python scripts/run_search_comparison.py
uv run --no-sync --python 3.13 python scripts/run_ablation.py
```

The first writes the matched-budget trajectories and summary. The second
writes the ablation metrics and efficiency figures. Both use the same
synthetic objective and a deterministic proposer. See the
[results guide](results.md) for the output names and interpretation.

For a fork, update the [manuscript configuration](manuscript/config.yaml),
the [domain profile](../domain_profile.yaml), the
[experiment plan](../experiment_plan.yaml), and the
[citation metadata](../CITATION.cff). The manuscript's `experiment` block
mirrors the code defaults. To change the simulation, edit
`SyntheticObjective` and `SearchConfig`, then update the mirror and rerun
the numeric regression tests.

Follow the [pinned build](manuscript-build.md) to regenerate evidence and
render the manuscript in PDF and HTML.
