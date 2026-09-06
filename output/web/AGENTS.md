# AGENTS.md — `template_autoscientists/output/web`

> Generated 2026-08-29 during the ongoing-docs fleet pass. Description derived
> from the on-disk listing; semantics marked (unverified) where not confirmed
> by running code.

## Role

HTML web rendering of the manuscript.

## Layout

- Files: `_combined_manuscript.md`, `favicon.ico`, `index.html`, `manuscript__00_abstract.html`, `manuscript__01_introduction.html`, `manuscript__02_methodology.html`, `manuscript__03_results.html`, `manuscript__04_experimental_setup.html`, `manuscript__05_reproducibility.html`, `manuscript__06_scope_and_related_work.html`, `manuscript__07_conclusion.html`, `manuscript__99_references.html`

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
