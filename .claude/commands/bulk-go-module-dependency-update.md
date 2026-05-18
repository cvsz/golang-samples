---
name: bulk-go-module-dependency-update
description: Workflow command scaffold for bulk-go-module-dependency-update in golang-samples.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /bulk-go-module-dependency-update

Use this workflow when working on **bulk-go-module-dependency-update** in `golang-samples`.

## Goal

Updates Go module dependencies (e.g., go.opentelemetry.io/otel, go.opentelemetry.io/otel/sdk) across many subdirectories by modifying go.mod and go.sum files to new versions.

## Common Files

- `**/go.mod`
- `**/go.sum`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify outdated dependencies (often via automation, e.g., Dependabot).
- For each affected subdirectory, update the relevant dependency versions in go.mod.
- Run 'go mod tidy' or equivalent to update go.sum.
- Commit all changed go.mod and go.sum files together in a single commit.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.