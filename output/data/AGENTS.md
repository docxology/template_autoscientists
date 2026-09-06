# AGENTS.md — `template_autoscientists/output/data`

> Generated 2026-08-29 during the ongoing-docs fleet pass. Description derived
> from the on-disk listing; semantics marked (unverified) where not confirmed
> by running code.

## Role

Generated analysis data (CSV/NPZ/JSON) emitted by project analysis stages.

## Layout

- Files: `ablation.json`, `publication_ledger.json`, `search_comparison.json`

## Invariants

- Local-only path under `projects/ongoing/` (root `.gitignore` rule
  `projects/*`) — never commit. Repo-wide policy: see
  `/Volumes/external_drive/Git/template/projects/ongoing/AGENTS.md`.
- Generated outputs in these trees are regenerable via the repo's canonical
  pipeline; do not hand-edit artifacts to "fix" results.
- This repo lives in the public docxology mirror — anything written here
  becomes public once pushed to the repo's GitHub remote.

## Gotchas

- No silent omissions: if a child folder above is undocumented, that is a
  known gap of this auto-generated doc — replace it with a verified
  description when you work here.
