# Rebuild the AutoScientists manuscript

Install Git, uv, Pandoc 3.14 with pandoc-crossref 0.3.26b, and XeLaTeX with
the [required TeX packages](https://github.com/docxology/template/blob/87704feae0a4490ef7dad9c931d268e8c30273c2/docs/usage/output-formats.md).
Use a disposable checkout to preserve the tracked release snapshot separately
from newly computed results.

From a clean checkout of this repository:

```sh
set -e
project_root="$(pwd -P)"
renderer="$(mktemp -d)/template"
git clone https://github.com/docxology/template.git "$renderer"
git -C "$renderer" checkout --detach 87704feae0a4490ef7dad9c931d268e8c30273c2
mkdir -p "$renderer/projects/working"
project_copy="$renderer/projects/working/template_autoscientists"
git clone --no-hardlinks "$project_root" "$project_copy"
git -C "$project_copy" checkout --detach "$(git -C "$project_root" rev-parse HEAD)"

cd "$renderer"
uv sync --locked --no-dev

cd "$project_copy"
uv sync --locked --python 3.13 --extra dev
uv run --no-sync --python 3.13 pytest -q -m 'not requires_ollama' --cov=src --cov-fail-under=90
uv run --no-sync --python 3.13 python scripts/run_search_comparison.py
uv run --no-sync --python 3.13 python scripts/run_ablation.py

cd "$renderer"
uv run --no-sync python scripts/pipeline/stage_03_render.py --project working/template_autoscientists
uv run --no-sync python scripts/pipeline/stage_04_validate.py --project working/template_autoscientists
```

In the disposable project copy, inspect
`output/pdf/template_autoscientists_combined.pdf`, `output/web/index.html`,
and the validation and provenance receipts under `output/reports/`.
The build renders the [nine authored sections](manuscript/README.md) and
uses newly generated JSON results and three figure PNGs. The offline
transcript fixture verifies a separate replay API. A provider call is outside
the build and evidence.
