# Agent Instructions — AutoScientists

## Operational Constraints

1. **Never mock.** All tests use real data and real computation.
2. **Keep scripts thin.** Business logic belongs in `src/`.
3. **Deterministic by default.** Tests must pass without network access,
   without LLM calls, and without any live agent backend.
4. **Honest reporting.** Effect-size tables must include null results.
   Do not suppress negative findings.
5. **Ablation safety.** Running `scripts/run_ablation.py` should never
   modify source code — only produce output figures and data.

## Workflow

Commands below are relative to this repository's root, matching README.md.

1. Edit coordination logic in `src/`.
2. Regenerate ablation results: `uv run python scripts/run_ablation.py`.
3. Verify: `uv run pytest tests/ --cov=src --cov-fail-under=90`.
4. Regenerate monorepo pipeline outputs (template monorepo only — `scripts/pipeline/` is a monorepo-root path, not project-local; this repository has no `scripts/pipeline/`): `uv run python scripts/pipeline/stage_02_analysis.py --project templates/template_autoscientists`.
