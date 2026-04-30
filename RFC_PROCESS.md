# RFC Process — Envelope Team Definition Schema

This document describes how changes to the Envelope Team Definition Schema are proposed, reviewed, and accepted. Following this process is required for all non-trivial changes to `team-v1.json`.

---

## Why an RFC process?

The schema is a public contract. Once a field is published in a stable release, external tools, runtimes, and teams may depend on it. An RFC process ensures:

- Changes are intentional, not accidental
- The community can comment before anything is locked
- The decision trail is visible and permanent
- Envelope's core team retains clear authority while remaining accountable

---

## What requires an RFC?

**Requires an RFC:**
- Adding a new top-level field to the schema
- Removing or renaming any existing field
- Changing the type, format, or allowed values of an existing field
- Changing the backwards-compatibility commitment itself

**Does not require an RFC:**
- Fixing a typo in a `description` string
- Adding a new allowed `enum` value that doesn't break existing values
- Improving inline documentation or examples
- Adding a new `$def` type that is not yet referenced by any schema field

If you are unsure, open a Discussion on this repo and ask before starting an RFC.

---

## Lifecycle

```
Draft → Open for Comment → Accepted / Rejected → Implemented
```

| Stage | What happens |
|---|---|
| **Draft** | Author opens a GitHub Issue using the RFC template. Status: `rfc: draft` |
| **Open for Comment** | Envelope core team marks the issue `rfc: open`. Community has 14 days to comment. |
| **Accepted** | Core team closes discussion and labels `rfc: accepted`. A PR implementing the change is opened against `main`. |
| **Rejected** | Core team closes the issue with `rfc: rejected` and a written reason. |
| **Implemented** | PR is merged. Schema version is bumped. CHANGELOG.md is updated. |

---

## How to open an RFC

1. Open a new **Issue** in this repository
2. Use the title format: `RFC: <brief description of proposed change>`
3. Fill in the following sections in the issue body:

```
## Motivation
Why is this change needed? What problem does it solve? Link to any real-world examples.

## Proposed change
Describe the exact field addition, removal, or modification. Include the updated JSON Schema snippet.

## Alternatives considered
What other approaches were evaluated and why were they rejected?

## Backwards compatibility
Is this change backwards-compatible? If not, explain what breaks and what the migration path is.

## Impact on tooling
Does this affect the CLI, the conform suite, or any known third-party tooling?
```

---

## Backwards-compatibility commitment

**Within a major version (e.g. v1.x), the schema is additive only.**

- Fields may be added (new optional fields are always safe)
- Fields may not be removed
- Field types may not be narrowed
- Enum values may not be removed

A breaking change requires a new major version (`v2`). The old version remains available at its original URL indefinitely.

**Exception:** Security issues may require a breaking change at any version. The core team will document the issue, give as much notice as possible, and provide a migration guide.

---

## Merge authority

During v1, merge authority rests with the **Envelope core team**.

As the ecosystem matures, governance will evolve. The goal is to move toward a model where significant external adopters have a formal voice in the RFC process. Any changes to governance will themselves go through a public RFC.

---

## Version numbering

The schema follows [Semantic Versioning](https://semver.org):

| Change type | Version bump |
|---|---|
| New optional field | Patch (`1.0.x`) |
| New required field (breaking) | Major (`2.0.0`) |
| Field removal (breaking) | Major (`2.0.0`) |
| Type change (breaking) | Major (`2.0.0`) |
| Documentation / description fix | Patch (`1.0.x`) |

The npm package (`@envelope/schema`) version tracks the schema version.

---

## First RFC — proof of concept

The first internal schema change should go through this process as a proof of concept, even if the change is minor. This validates the process before it is needed for something important.
