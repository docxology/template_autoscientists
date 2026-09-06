# `scripts/`

Thin orchestrators: argparse/path bootstrap, logging, and a single delegated
call into a `src/` entrypoint. All business, data, plot, and analysis logic
lives in `src/` (importable and tested by `tests/`).

## Inventory

| Script | Purpose | Delegates to | Run command |
|--------|---------|--------------|-------------|
| `run_ablation.py` | Per-mechanism ablation of the coordination loop (each mechanism switched off in turn) | `src.ablation` (`run_ablations`, `build_ablation_payload`), `src.figures` (`write_ablation_figure`, `write_efficiency_figure`, `write_figure_registry`) | `uv run python scripts/run_ablation.py` |
| `run_search_comparison.py` | Coordinated vs single-thread baseline under a matched sequential experiment budget | `src.comparison` (`build_objective`, `run_comparison`, `build_comparison_payload`), `src.figures` (`write_comparison_figure`, `write_figure_registry`) | `uv run python scripts/run_search_comparison.py` |
| `hermes_proposer.py` | Live `HermesProposer` adapter (Ollama-served Hermes model). Import-only module — no CLI; re-exported lazily by `src.__init__` and imported by `tests/test_agents.py` / `tests/test_hermes_live.py` | `src.agents` (`_extract_json`), `src.state`; lazy `infrastructure.llm` (template-monorepo-only, `# pragma: no cover`) | Not run directly — exercised by `uv run pytest tests/test_hermes_live.py -m requires_ollama` (opt-in) |

Outputs land in `output/figures/` (`ablation.png`, `ablation_efficiency.png`,
`search_comparison.png`, `figure_registry.json`) and `output/data/`
(`ablation.json`, `search_comparison.json`).

See the project [`../AGENTS.md`](../AGENTS.md) and [`../docs/quickstart.md`](../docs/quickstart.md).
