# Quickstart — AutoScientists

```bash
# Run the full coordinated search vs single-thread baseline (deterministic)
uv run python scripts/run_search_comparison.py

# Run ablation study (all mechanisms toggled one by one)
uv run python scripts/run_ablation.py

# Run tests
uv run pytest tests/ --cov=src --cov-fail-under=90
```

Outputs land in `output/figures/` (ablation metric/efficiency plots) and
`output/data/` (search results JSON).
