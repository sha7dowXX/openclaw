```markdown
# openclaw Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill documents the key development patterns, coding conventions, and workflows used in the `openclaw` TypeScript codebase, which is built on the Express framework. It covers file naming, import/export styles, commit conventions, test organization, and specialized workflows for test refinement, deduplication, extension optimization, and SDK surface management. Use this guide to contribute effectively and maintain consistency across the project.

## Coding Conventions

- **File Naming:**  
  Use `camelCase` for file names.  
  _Example:_  
  ```
  userAuth.ts
  onboardNonInteractive.test.ts
  ```

- **Import Style:**  
  Use **relative imports** for internal modules.  
  _Example:_  
  ```typescript
  import { runCommand } from './runCommand';
  import { Agent } from '../agents/agent';
  ```

- **Export Style:**  
  Use **named exports**.  
  _Example:_  
  ```typescript
  // Good
  export function runCommand() { ... }
  export const AGENT_TYPE = 'core';

  // Avoid default exports
  ```

- **Commit Messages:**  
  Follow the **conventional commit** format.  
  - Prefixes: `test`, `perf`, `fix`, `tests`
  - Keep messages concise (~43 chars on average).  
  _Example:_  
  ```
  fix: handle missing provider in onboarding flow
  test: split auth-choice tests for clarity
  ```

## Workflows

### Refine or Add Test Coverage for Command or Feature
**Trigger:** When you want to improve, isolate, or expand test coverage for a command or feature.  
**Command:** `/refine-test`

1. Identify the command or feature needing more or better tests.
2. Edit or create the relevant test files, usually in `src/commands/` or `src/agents/`.
3. Adjust mocks, fixtures, or test imports as needed.
4. Move or split test cases between files for better isolation if necessary.

_Files involved:_  
- `src/commands/*.test.ts`
- `src/commands/*/*.test.ts`
- `src/commands/*/*.ts`
- `src/agents/*.test.ts`
- `src/agents/*.ts`

_Example:_  
```typescript
// src/commands/onboard.test.ts
import { onboard } from './onboard';

test('handles missing provider', () => {
  // ...test logic
});
```

---

### Merge or Trim Duplicate Test Cases
**Trigger:** When you want to reduce redundant test coverage or consolidate similar tests.  
**Command:** `/dedupe-tests`

1. Identify duplicate or overlapping test cases (e.g., onboarding, auth-choice).
2. Edit or remove redundant test files or cases.
3. Merge unique cases into a single file or suite.

_Files involved:_  
- `src/commands/onboard-non-interactive.provider-auth.test.ts`
- `src/commands/auth-choice.test.ts`
- `src/commands/onboard-non-interactive.gateway.test.ts`
- `src/commands/onboard-non-interactive/api-keys.test.ts`

_Example:_  
```typescript
// Merge onboarding provider and gateway tests into one file
```

---

### Extension Test and Implementation Optimization
**Trigger:** When you want to improve performance or maintainability of extension tests or runtime.  
**Command:** `/optimize-extension-tests`

1. Identify the extension or plugin needing optimization.
2. Edit test and implementation files within the extension's directory.
3. Narrow imports, remove unnecessary waits, or optimize test boundaries.

_Files involved:_  
- `extensions/*/src/*.ts`
- `extensions/*/src/*.test.ts`
- `extensions/*/src/**/*.ts`

_Example:_  
```typescript
// Remove unnecessary setTimeout in extension test
```

---

### Core Command or Agent Hotspot Reduction
**Trigger:** When you want to reduce complexity or improve maintainability in core command/agent code.  
**Command:** `/reduce-hotspot`

1. Identify hotspot in core command or agent logic.
2. Edit both implementation and test files to refactor, split, or optimize.
3. Move logic between files or isolate responsibilities as needed.

_Files involved:_  
- `src/commands/*.ts`
- `src/commands/*.test.ts`
- `src/agents/*.ts`
- `src/agents/*.test.ts`

_Example:_  
```typescript
// Split large agent file into smaller, focused modules
```

---

### Plugin SDK Surface or Import Refinement
**Trigger:** When you want to optimize or clarify the plugin SDK's API surface.  
**Command:** `/refine-plugin-sdk`

1. Edit plugin SDK implementation files to narrow or clarify exports.
2. Update related documentation and scripts.
3. Regenerate or update SDK API baselines as needed.

_Files involved:_  
- `src/plugin-sdk/*.ts`
- `scripts/lib/plugin-sdk-*.json`
- `docs/plugins/*.md`
- `docs/.generated/plugin-sdk-api-baseline.sha256`

_Example:_  
```typescript
// src/plugin-sdk/index.ts
export { PluginContext, PluginAPI } from './core';
// Remove unused exports
```

## Testing Patterns

- **Framework:** [vitest](https://vitest.dev/)
- **Test File Pattern:** `*.test.ts`
- **Location:** Tests are placed alongside implementation files, often in `src/commands/` and `src/agents/`.
- **Test Example:**
  ```typescript
  // src/commands/userAuth.test.ts
  import { authenticate } from './userAuth';

  test('returns error for invalid token', () => {
    // ...test logic
  });
  ```

- **Mocking:**  
  Mocks and fixtures are adjusted as needed for test isolation and coverage.

## Commands

| Command                   | Purpose                                                          |
|---------------------------|------------------------------------------------------------------|
| /refine-test              | Refine, split, or add test coverage for a command or feature     |
| /dedupe-tests             | Merge or trim duplicate or overlapping test cases                |
| /optimize-extension-tests | Optimize extension/plugin tests and implementation files          |
| /reduce-hotspot           | Refactor or reduce hotspots in core command/agent logic          |
| /refine-plugin-sdk        | Refine/narrow plugin SDK import surfaces and update documentation|
```
