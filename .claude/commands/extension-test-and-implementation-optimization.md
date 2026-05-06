---
name: extension-test-and-implementation-optimization
description: Workflow command scaffold for extension-test-and-implementation-optimization in openclaw.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /extension-test-and-implementation-optimization

Use this workflow when working on **extension-test-and-implementation-optimization** in `openclaw`.

## Goal

Optimizes, refines, or speeds up extension tests and implementation files, often by narrowing imports, reducing polling, or improving test boundaries.

## Common Files

- `extensions/*/src/*.ts`
- `extensions/*/src/*.test.ts`
- `extensions/*/src/**/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify extension or plugin needing optimization.
- Edit multiple test and implementation files within the extension's directory.
- Narrow imports, remove unnecessary waits, or optimize test boundaries.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.