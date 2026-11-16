# hep-agent-bench-rubric

The rubric for **hep-agent-bench**: how its tasks are built and graded. hep-agent-bench gives an AI agent a real, self-contained HEP software problem; the rubric says that give an AI agent a real, self-contained HEP software how its result is checked on held-out data and turned into a score with expert-defined metrics.

A task is a [Harbor](https://harborframework.com) task (the format behind Terminal-Bench), plus a small set of HEP rules for the things Harbor leaves open: continuous scores, held-out data, timing on fixed hardware, baseline integrity and physics validation.

| Document | Covers |
|---|---|
| [task-format.md](task-format.md) | Directory layout, `task.toml` metadata, data, canary |
| [grading.md](grading.md) | Correctness gate, scores, `metrics.json`, timing, baseline integrity |

**Version 0.2** (draft). Derived from the first two tasks, [`frnn-exact-optimization`](https://github.com/hep-cce2/hep-agent-bench/tree/main/tasks/frnn-exact-optimization) (an optimisation task) and `analysis/qa_1_offline` (a set of analysis questions). Expect changes as the Celeritas and RNTuple tasks arrive. A task declares the version it follows (`hep_agent_bench_rubric` in `task.toml`), and the grader writes it into `metrics.json` (`rubric_version`).

Changes in 0.2: renamed from hep-agent-bench-spec; the `fraction-passed` score; baseline, expert, `gain` and `hardware` apply only to gain-based scores; graders copied into `solution/` must be checked for drift.

Related repositories:
- [hep-agent-bench](https://github.com/hep-cce2/hep-agent-bench): the tasks.
- [hep-agent-bench-tools](https://github.com/hep-cce2/hep-agent-bench-tools): the `hepbench` Python package that implements the grading rules. Tasks should use it rather than copy code.

## Changing the rubric

Open an issue or PR here. A rule belongs in the rubric once two tasks need it; until then it lives in the task. Each change that affects graders bumps the version and gets a matching `hepbench` release.

The words MUST, SHOULD and MAY are used as in RFC 2119.
