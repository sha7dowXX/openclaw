---
name: refine-or-add-test-coverage-for-command-or-feature
description: Workflow command scaffold for refine-or-add-test-coverage-for-command-or-feature in openclaw.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /refine-or-add-test-coverage-for-command-or-feature

Use this workflow when working on **refine-or-add-test-coverage-for-command-or-feature** in `openclaw`.

## Goal

Refines, splits, or adds test coverage for a specific command, feature, or edge case, often by narrowing mocks, splitting tests, or moving cases between files.

## Common Files

- `src/commands/*.test.ts`
- `src/commands/*/*.test.ts`
- `src/commands/*/*.ts`
- `src/agents/*.test.ts`
- `src/agents/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify command or feature needing test refinement or coverage.
- Edit or create corresponding test files (often in src/commands/ or src/agents/).
- Adjust mocks, fixtures, or test imports as needed.
- Sometimes move or split test cases between files for isolation.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.