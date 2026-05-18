```markdown
# golang-samples Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides guidance on contributing to the `golang-samples` repository, which demonstrates Go code samples with TypeScript-based tooling and conventions. It covers file naming, import/export styles, commit message patterns, dependency update workflows, and testing conventions.

## Coding Conventions

### File Naming
- Use **camelCase** for file names.
  - Example: `sampleHandler.ts`, `userService.ts`

### Import Style
- Use **relative imports** for internal modules.
  - Example:
    ```typescript
    import { fetchData } from './dataFetcher';
    ```

### Export Style
- Use **named exports**.
  - Example:
    ```typescript
    export function processSample() { ... }
    export const SAMPLE_CONSTANT = 42;
    ```

### Commit Messages
- Follow **conventional commit** patterns.
- Use prefixes such as `chore`.
- Keep commit messages concise (average ~75 characters).
  - Example:
    ```
    chore: update otel dependencies in all modules
    ```

## Workflows

### Bulk Go Module Dependency Update
**Trigger:** When dependencies (especially shared ones) need to be updated across all or many Go sample directories, often triggered by Dependabot or similar automation.  
**Command:** `/update-deps-all`

1. **Identify outdated dependencies**  
   Use automation tools (e.g., Dependabot) or manual checks to find outdated dependencies such as `go.opentelemetry.io/otel` and `go.opentelemetry.io/otel/sdk`.

2. **Update dependency versions**  
   For each affected subdirectory, update the relevant dependency versions in `go.mod`.

3. **Run `go mod tidy`**  
   Execute `go mod tidy` (or equivalent) in each directory to update `go.sum` and clean up unused dependencies.

4. **Commit changes**  
   Commit all changed `go.mod` and `go.sum` files together in a single commit. Use a conventional commit message, e.g.:
   ```
   chore: update otel dependencies in all modules
   ```

**Files Involved:**
- `**/go.mod`
- `**/go.sum`

**Frequency:** ~2-4 times per month

**Example Command:**
```sh
/update-deps-all
```

## Testing Patterns

- Test files follow the pattern: `*.test.*`
  - Example: `sampleHandler.test.ts`
- The specific testing framework is unknown, but standard TypeScript test conventions apply.
- Place test files alongside the code they test or in a dedicated `__tests__` directory.

**Example Test File:**
```typescript
// sampleHandler.test.ts
import { processSample } from './sampleHandler';

describe('processSample', () => {
  it('should process input correctly', () => {
    expect(processSample('input')).toBe('expectedOutput');
  });
});
```

## Commands

| Command         | Purpose                                                        |
|-----------------|----------------------------------------------------------------|
| /update-deps-all| Bulk update Go module dependencies across all sample directories|
```
