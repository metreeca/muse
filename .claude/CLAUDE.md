> [!CAUTION]
>
> - **ONLY** modify code when explicitly requested or clearly required.
> - **NEVER** make unsolicited changes or revert **unrelated** user edits.
> - **ALWAYS** monitor IDE diagnostics when working on a file

> [!CAUTION]
> Activating and following skill guidance is **MANDATORY** for every task. Before starting any work, identify and
> activate all relevant skills. Skill instructions are binding and override default behaviours. When in doubt about
> whether skill guidance is current, relevant skills MUST be reloaded.

# Overview

`@metreeca/muse` is a standalone, general-purpose monorepo collecting the AI task framework core and its provider
packages, each sitting directly under `packages/` (for example `packages/muse/`).

Jobs run under the `@metreeca/gear` executor: this repository contributes model services and tasks, **NEVER** an
execution runtime of its own. Reach for `executor`, `bind` and `service` from `@metreeca/gear` rather than
reimplementing them, and keep the service contracts compatible with the ones `@metreeca/gear` already resolves.

# References

- [@metreeca/core](https://github.com/metreeca/core) - Core utilities and shared types
- [@metreeca/flow](https://github.com/metreeca/flow) - Composable async iterable processing
- [@metreeca/tape](https://github.com/metreeca/tape) - Simplified facade for the LogTape logging framework
- [@metreeca/gear](https://github.com/metreeca/gear) - Ready-made tasks and shared services for ETL jobs, supplying the
  job executor and service locator this repository builds on

# NPM Scripts

- **`npm run clean`** - Remove build artifacts and dependencies (dist, docs, node_modules)
- **`npm run setup`** - Install dependencies
- **`npm run build`** - Build TypeScript and generate TypeDoc documentation
- **`npm run check`** - Run Vitest test suite
- **`npm run proof`** - Build documentation and start static server

# Package Layout

The root `package.json` `workspaces` glob (`packages/*`) covers the framework packages, each in its own directory
immediately under `packages/` (for example `packages/muse`).

Provider packages are self-contained leaves named after the vendor, not the cloud platform or the model family:
`muse-google`, not `muse-gcp` or `muse-gemini`. Each pulls in the core package transitively and only the SDK its own
provider needs.

# Shared Utilities

Reach for `@metreeca/core` before writing a helper: its `strings`, `numbers`, `arrays` and `structures` entry points
already cover text tidying, escaping, splitting and templating alongside the common collection and value operations. A
hand-rolled equivalent duplicates tested code and drifts from it, missing the edge cases the shared one handles.

Keep a local helper only where the shared one genuinely doesn't fit, and record in its doc comment what the difference
is, so the next reader doesn't take it for an oversight.

# Service Resolution

Calls to `service()` are **NEVER** inlined into a larger expression: always bind the resolved instance to a `const` on a
line of its own, then use it. This keeps the resolution point visible, since it depends on the enclosing execution
rather than on the surrounding expression.

```typescript
const model = service(getModel); // ✅
const answer = lazy(async () => model(await prompt(question)));

const answer = lazy(async () => service(getModel)(await prompt(question))); // ❌
```

# Testing

The root `vitest.config.ts` aliases all workspace `@metreeca/muse*` packages to their TypeScript source via regex, so
vitest transpiles directly from `src/` without requiring a prior build step. The resolver maps each `@metreeca/muse*`
specifier to `packages/<package>/src`; the aliases are convention-based and require no manual updates when adding
packages or subpath exports.

# Version Management

All workspace packages share the root `package.json` version. Beyond the `version` fields the release flow already
cascades, update the internal `@metreeca/muse*` dependency ranges in every `packages/**/package.json` to match.

When adding, removing, or renaming packages, update the package table in the root `README.md` Usage section to match.
