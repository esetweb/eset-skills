# Example ADR (illustrative)

A short, fictional ADR showing tone, density and Markdown shape. All names and numbers are made up; a real ADR uses facts verified against the codebase.

---

# ADR 0007: Use Vitest instead of Jest for unit tests in web apps

**Status:** Proposed

**Impact level:** Low

**Date:** 15 Oct 2026

**Authors:** <name>

## 1. Context

The web apps run unit tests with Jest through a Babel transform, while the build already uses Vite. Every app keeps two transform pipelines in sync, and ESM only dependencies need manual `transformIgnorePatterns` entries.

The test setup is coupled to:

- `babel.config.cjs`, which exists only for Jest,
- `jest.config.js` per app,
- a CI step that runs the suite once per app.

Scope: the unit test runner of the web apps. End to end tests are not affected.

## 2. Decision

Each web app will run unit tests with Vitest, using the app's existing `vite.config`.

Scope boundary: this covers unit and component tests only. It does not change end to end tooling.

Secondary benefit, not the primary reason: faster watch mode.

## 3. Decision drivers

- **One pipeline**
  - Tests use the same Vite transform as the build, so no Babel config is kept only for Jest.
- **ESM support**
  - ESM only packages work without manual ignore patterns.
- **Low migration cost**
  - Vitest keeps the Jest API (`describe`, `it`, `expect`), so most tests run unchanged.

## 4. Alternatives considered

### 4.1. Keep Jest

Rejected because:

- the second transform pipeline stays and keeps drifting from the build;
- ESM only dependencies keep needing manual patterns.

### 4.2. Node's built in test runner

Rejected for now because:

- no component test ecosystem comparable to Testing Library setups with jsdom helpers.

Reconsider when it supports DOM environments out of the box.

## 5. Consequences

### ✅ Positive

- One transform pipeline for build and tests.
- Fewer config files per app.

### ⚠️ Negative / Trade-offs

- **Migration effort per app**
  - The team that owns each app carries it; mitigated by migrating when an app's tests are next touched.
- **Jest specific mocks may need rewriting**
  - Mitigated by a short migration guide in the first migrated app.

## 6. Implementation and risk mitigation

Before the first app is migrated, the team must define:

- the shared Vitest config and a migration guide;
- the CI step that replaces the Jest one;
- review with the owners of the apps.

The team owning each app stays accountable for its tests after release.

## 7. Decision outcome

**Status:** Pending adoption

**Outcome if approved:** web apps move from Jest to Vitest, starting with new apps.

**Implementation notes:**

- Create the tracking story <TODO: Jira story>.
- Migrate one pilot app and write the migration guide.

## 8. References

- Jira story: <TODO: Jira story>
- Vitest documentation: <TODO: link>
