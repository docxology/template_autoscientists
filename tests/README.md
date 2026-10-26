# `tests/`

No-mocks test suite for the coordination core.

**Contents.** `test_*.py` cover search, ranking, confirmation, dead-ends, stagnation, agents, objective, and state with real deterministic runs.

**Contract.** Run: `uv run pytest tests -m "not requires_ollama" --cov=src --cov-fail-under=90`. In the template monorepo the same gate is `uv run python scripts/pipeline/stage_01_test.py --project templates/template_autoscientists --project-only` (monorepo-root path, absent here).

See the project [`../AGENTS.md`](../AGENTS.md).
