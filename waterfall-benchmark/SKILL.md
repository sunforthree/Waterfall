---
name: waterfall-benchmark
description: Use when a team wants to create, update, or interpret a Waterfall agent benchmark or interactive web demo for recurring workflows, compare models or reasoning settings, or investigate a candidate model switch using per-run quality, latency, and cost.
---

# Waterfall Benchmark

Waterfall compares agent configurations on a versioned task suite. Each attempt has its own record and mark. The chart is a view of the records and can be regenerated in any harness.

## Establish the comparison

Find the suite, historical run records, scoring policy, and existing harness. Identify the switch decision and the team’s quality, latency, and cost criteria. Use one case ID per repeatable task, with versioned instructions, starting state, tools and permissions, limits, and acceptance checks. Use one configuration ID per combination of model snapshot, provider-native reasoning setting, harness, prompts, tool adapters, and retry policy.

Pair configurations on the same cases, state, budgets, and grader. A changed adapter or prompt makes the comparison configuration-level. Start with a few repeated runs to screen settings and use a representative paired suite to confirm a switch. Report the evidence as exploratory when only pilot data is available.

## Record and plot attempts

| Field | Treatment |
|---|---|
| Identity | Record attempt ID, case and suite versions, configuration ID, start timestamp, trial index, and artifact or trace reference when available. |
| Time | Use seconds from agent start to terminal state, including in-workflow retries, waits, and review. Record benchmark-only grading time separately. Plot with time increasing downward. |
| Quality and verdict | Record rubric version, quality score, and acceptance verdict separately. Plot higher quality to the right. Use an unscored lane if a score is missing. Mark missing-time attempts in a status count. |
| Terminal status | Include agent timeouts and errors as unsuccessful valid attempts. Record independent host or evaluator faults as invalid, show the count, and rerun affected cases. |
| Optional metrics | Keep named units and measurement boundaries for cost, tokens, human review, or checkpoints. Preserve missing values. Show extra metrics in tooltips, panels, or a labeled optional third axis. |

Use one equal-sized mark per attempt, with a labeled legend for color and shape. When color identifies the model, keep its reasoning settings in the same color and distinguish settings by shape or labels where needed. Keep each palette's model mapping fixed across filters. Expose overlap counts or individual records. Preserve the shared scales when faceting. Append new records. Regrade saved outputs under a common rubric before pooling versions, or rerun a matched slice when regrading is unavailable. Preserve prior grades.

## Offer an interactive web demo

When people need to explore the benchmark, use a website as a view of the existing run records. A static browser page can read an exported dataset and work within any harness. Draw the point cloud from each run's recorded quality and elapsed time. If the points naturally form a cascade, let them define the shape. Use clearly labeled synthetic records for an illustrative waterfall silhouette.

Let readers filter configurations on shared scales and inspect a point by pointer, touch, or keyboard. For run history, use start timestamps to filter by model and an inclusive date range. Label the time zone, summarize the matching attempts, and break out reasoning settings so the pooled summary remains interpretable. Show the attempt ID, configuration, rubric, elapsed time, quality, verdict, status, and cost when available. Keep timed-out attempts accessible in the unscored lane and surface records with missing time in a status count. If readers can adjust a time target, update the target guide and on-time acceptance counts. Preserve the original verdicts and include failed-attempt costs in the cost per acceptance. Check these interactions and the small-screen layout before sharing the demo.

For dense point clouds, a timeline can select a whole period. Offer date fields as a keyboard-accessible alternative to dragging. Keep points at their original coordinates. If dimmed points show the full dataset for context, label them and exclude them from the selected-period counts, summary, and attempt navigation.

## Report the decision

Show the case coverage, valid and invalid counts, acceptance, latency, and cost per accepted outcome. Divide known spend on valid attempts, including failures, by accepted outcomes. If spend is incomplete or acceptances are zero, mark the ratio unavailable. Show independently invalid spend separately. Compare paired case-level results when repetitions differ.

For example, if a candidate has 7 accepts in 8 completed cases, plus one agent timeout and one independent host outage, the valid count is 9 and the provisional figure is 7/9 on that rubric. Plot the timeout at its observed duration in the unscored lane and rerun the outage. Compare to the incumbent only after aligning cases, rubric, and cost scope. A single favorable high-reasoning run remains a pilot observation.
