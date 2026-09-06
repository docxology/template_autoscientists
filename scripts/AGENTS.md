# `scripts/` — Agent Guide

Thin orchestrators ONLY. The contract: path bootstrap (shared sibling pattern
below), logging, and a single delegated call into a `src/` entrypoint.
Business, data, plot, and analysis logic lives in `src/` — importable and
tested by `tests/`. Scripts never re-implement it.

## Inventory

| Script | Purpose | Delegates to | Run command |
|--------|---------|--------------|-------------|
| `run_ablation.py` | Per-mechanism ablation; writes figures + JSON | `src.ablation`, `src.figures` | `uv run python scripts/run_ablation.py` |
| `run_search_comparison.py` | Coordinated vs single-thread baseline, matched budget; writes figure + JSON | `src.comparison`, `src.figures` | `uv run python scripts/run_search_comparison.py` |
| `hermes_proposer.py` | Live `HermesProposer` adapter (Ollama). Import-only module — no CLI | `src.agents`, `src.state`; lazy `infrastructure.llm` (monorepo-only) | `uv run pytest tests/test_hermes_live.py -m requires_ollama` (opt-in) |

## Gotchas

- **Path bootstrap is mandatory.** Every script that imports `src.*` must first
  insert `PROJECT_ROOT` (repo root), `PROJECT_ROOT / "src"`, and `REPO_ROOT`
  into `sys.path` (`PROJECT_ROOT = Path(__file__).resolve().parent.parent`,
  `REPO_ROOT = PROJECT_ROOT.parents[2]`), marking the `src` imports
  `# noqa: E402`. Scripts must run from any cwd, not just the repo root; never
  rely on the caller's cwd or an installed package.
- **`hermes_proposer.py` is a library, not a CLI.** `src/__init__.py` lazily
  re-exports `HermesProposer` via `from hermes_proposer import HermesProposer`,
  which requires `scripts/` on `sys.path` (`tests/conftest.py` adds it;
  `pyproject.toml` `pythonpath` does not). Its `infrastructure.llm` imports are
  lazy and exist only in the template monorepo — keep them lazy so `src/` and
  the deterministic suite stay infrastructure-free.
- **Outputs are tracked.** Both orchestrators write into `output/figures/` and
  `output/data/`; regenerating rewrites tracked files.
- **Live path is opt-in.** `requires_ollama` tests skip cleanly without Ollama;
  nothing here may add a network dependency to the deterministic suite.
