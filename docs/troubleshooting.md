# Troubleshooting

- If figures are missing, run both analysis scripts in the
  [quick start](quickstart.md). They produce the comparison and both
  ablations under `output/figures/`.
- If the coverage run attempts to contact a provider, use the exact marker
  selection in the quick start. The offline replay checks use a local fixture.
- If a quoted metric changes, inspect the comparison and ablation JSON files
  and the inputs mirrored in the manuscript configuration. Verify the change
  with the numerical regression tests before updating claims.
- If PDF or HTML validation fails, check the versions and
  `output/reports/` with the [pinned build guide](manuscript-build.md).
