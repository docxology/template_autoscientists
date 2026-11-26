# AutoScientists documentation

- [Quick start](quickstart.md) installs the locked environment, runs tests,
  and reproduces the comparison and ablations locally.
- [Architecture](architecture.md) describes the search loop and the five
  coordination mechanisms.
- [Results](results.md) interprets the stored comparison and plots.
- [Manuscript](manuscript/README.md) indexes the paper’s source sections.
  The [build guide](manuscript-build.md) regenerates evidence and renders it.
- [Testing](testing_philosophy.md) and [troubleshooting](troubleshooting.md)
  cover coverage, replay, and common failures.
- [Contributor instructions](agent_instructions.md) and [backlog](backlog.md)
  cover maintenance.

The simulation uses a synthetic objective and a rule-based proposer. The
tracked release artifacts preserve a prior run. The bundled transcript is a
separate synthetic replay fixture used to verify envelope validation.
