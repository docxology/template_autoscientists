---
name: template-autoscientists
description: AutoScientists coordination-mechanism testbed — dead-end registry, noise-band confirmation, effect-size ranking, stagnation-driven reorganization, honest null reporting.
version: 0.1.0
author: docxology
license: MIT
tags: [exemplar, coordination, agents, ablation]
---

# template-autoscientists

Project-scoped skill for the in-repo exemplar at
`projects/templates/template_autoscientists/`. Load this when working inside the project.

## When to Use

- Working inside the `template_autoscientists` exemplar — running scripts, editing source,
  or regenerating outputs.
- Forking this exemplar as the starting scaffold for a new research project.
- Validating that the exemplar's contracts (thin-orchestrator, layer boundaries,
  no-mocks testing) still hold after changes.

## Quick Reference

Follow the [standalone quick start](../../../docs/quickstart.md) for the
deterministic comparison, ablation, and coverage gate. Use the
[pinned manuscript build](../../../docs/manuscript-build.md) for PDF and HTML.

## Pitfalls

- **Keep scripts thin.** Business logic belongs in `src/` or shared
  `infrastructure/`, not in `scripts/`.
- **No mocks.** All tests must use real data, real files, and real
  computation.
- **Outputs are disposable.** Never hand-edit `output/` — regenerate from
  source and config.
- **Run from the repo root.** Commands assume the template monorepo root
  as working directory unless the child `AGENTS.md` states otherwise.

## Cross-refs

- Project contract: [`AGENTS.md`](../../../AGENTS.md)
- README: [`README.md`](../../../README.md)
- TODO: [`docs/backlog.md`](../../../docs/backlog.md)
- Exemplar roster: `projects/AGENTS.md` in the template monorepo (monorepo-only path, absent here)
