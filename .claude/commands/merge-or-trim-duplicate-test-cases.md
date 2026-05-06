---
name: merge-or-trim-duplicate-test-cases
description: Workflow command scaffold for merge-or-trim-duplicate-test-cases in openclaw.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /merge-or-trim-duplicate-test-cases

Use this workflow when working on **merge-or-trim-duplicate-test-cases** in `openclaw`.

## Goal

Merges, trims, or deduplicates overlapping or duplicate test cases, especially for onboarding, auth, or provider flows.

## Common Files

- `src/commands/onboard-non-interactive.provider-auth.test.ts`
- `src/commands/auth-choice.test.ts`
- `src/commands/onboard-non-interactive.gateway.test.ts`
- `src/commands/onboard-non-interactive/api-keys.test.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify duplicate or overlapping test cases (e.g., onboarding, auth-choice).
- Edit or remove redundant test files or cases.
- Merge unique cases into a single file or suite.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.