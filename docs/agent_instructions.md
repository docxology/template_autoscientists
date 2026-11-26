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

Run the [standalone commands](quickstart.md) to regenerate experiment
outputs and test changes. Use the [pinned render guide](manuscript-build.md)
to validate the updated manuscript from a disposable checkout.
