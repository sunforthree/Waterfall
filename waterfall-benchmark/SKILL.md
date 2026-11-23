---
name: waterfall-benchmark
description: Use when a team wants to build, maintain, or interpret a Waterfall agent benchmark or web demo for a recurring workflow, compare models or reasoning settings, or investigate a model switch using per-attempt quality, elapsed time, and cost.
---

# Waterfall Benchmark

Waterfall compares agent configurations on versioned tasks. Each attempt has one record and one mark. Higher quality plots farther right, and longer elapsed time plots lower. For the full method and worked example, use the [proposal](../WATERFALL.md) and [local demo source](../web-demo/dist/index.html) when supplied with this skill.

## Start with the available evidence

| Starting point | Deliverable |
|---|---|
| Demo only, or aggregate results | A browser preview with clearly labeled synthetic attempts and instructions to open it. Keep any reported aggregates separate and identify the run-level fields required to connect the harness. |
| Attempt export available | An adapter and a browser view derived from the records, plus a summary of coverage, exclusions, and missing fields. |
| Harness available and execution requested | Versioned cases and configurations, an attempt export, a browser view, and an evaluation summary. Use the existing runner and verifier. |

Identify the workflow, incumbent, candidate, acceptance checks, and budgets. Pair configurations on the same case versions, starting state, permissions, limits, and grading policy. Repeat cases where practical. A new prompt or adapter makes the result a configuration comparison. Treat a small pilot as exploratory.

## Export one record per attempt

- Record the attempt ID, suite and case versions, configuration ID, trial index, and start timestamp. A configuration identifies the model version, provider-native reasoning setting, harness, prompt, tool adapters, and retry policy.
- Record elapsed seconds from agent start to termination, including in-workflow waits, retries, and review. Track benchmark-only grading time separately. Record quality, verdict, terminal status, comparison validity, and verifier version independently.
- Count an agent timeout or error as a valid rejection. Record independent infrastructure or evaluator faults as invalid, show their count, and rerun affected cases. Preserve unknown fields as missing. Plot scored timeouts at their measured coordinates. Use an unscored lane for attempts with elapsed time and no score, and count missing-time attempts alongside the chart.
- Record cost with its currency and accounting boundary when available. Preserve prior grades when regrading under a new rubric. Import records idempotently by attempt ID. Share authorized fields and link protected artifacts through their existing access controls.

## Build the browser view

- **Point cloud.** Use the exported coordinates and fixed scales. Offer model multi-select and an inclusive date range based on the start timestamp in a named time zone. Support a timeline brush and keyboard-accessible date fields where useful. If the full cloud remains dimly visible, keep those context points outside the active counts and navigation.
- **Model comparison.** Use the same selected run records as Point cloud. Break out configurations and show the count, acceptance, a latency summary, and cost per accepted outcome. A time target can update the on-time count while preserving the verifier's verdict. Cost per accepted outcome divides all cost on valid attempts in the adjudicated cohort, including failures, by accepted outcomes. Mark it unavailable when adjudication or costs are incomplete, or no attempt was accepted. Report invalid spend separately.
- **Attempt details.** Expose the record through pointer, touch, and keyboard, including any overlapping attempts. Use a stable color per model within each theme. Distinguish reasoning settings with shapes or named rows. Synthetic fixtures may illustrate the waterfall shape. Actual run records determine the shape of the benchmark chart.

## Verify and hand off

Check counts and costs against a small known slice. Exercise a scored timeout, a missing score, an infrastructure fault, empty dates, and overlap navigation. Check that filtering or switching themes preserves coordinates, that a time-target change affects only the on-time measure, and that controls work on a narrow screen and by keyboard.

Hand off the browser entry point, data source or adapter, and run instructions. State which checks you ran and which comparisons the data supports. For a model-switch decision, report case coverage, acceptance denominators, pending grades, invalid counts, latency, and any limits on comparing cost or quality. Use paired case-level summaries when repeat counts differ.
