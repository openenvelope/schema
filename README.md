# Envelope Schema

The open JSON Schema for Envelope AI team definitions.

## What this is

Every Envelope team is defined by a `.envelope.json` file. This repository contains the canonical JSON Schema that validates those files. Builders reference it via the `$schema` field:

```json
{
  "$schema": "https://schema.openenvelope.org/team/v1.json",
  "name": "Support Tier",
  "slug": "support-tier",
  "version": "1.0.0",
  ...
}
```

The schema is an open specification (Apache 2.0). Any runtime can implement it. Platform implementors, validator authors, and editor plugin builders use this repo as the source of truth.

## Files

| File | Description |
|---|---|
| `team-v1.json` | Current schema. JSON Schema draft-07. `$id: https://schema.openenvelope.org/team/v1.json` |
| `CHANGELOG.md` | All schema changes, tagged by release |

## Using the schema

**Validate a team definition:**

```bash
npx ajv-cli validate -s team-v1.json -d your-team.envelope.json
```

**In Node.js / TypeScript:**

```typescript
import Ajv from 'ajv';
import schema from './team-v1.json';

const ajv = new Ajv();
const validate = ajv.compile(schema);
const valid = validate(myTeamDefinition);
if (!valid) console.log(validate.errors);
```

**npm packages:**

```bash
npm install @openenvelope/schema   # JSON Schema + TypeScript types (available now)
npm install @openenvelope/cli      # validate, diff, publish from the terminal (coming soon)
```

## Following updates

This repo uses [GitHub Releases](../../releases) for every schema version. Each release is tagged `vMAJOR.MINOR.PATCH` and includes the updated schema file plus a changelog entry.

To be notified of changes: **Watch → Custom → Releases** in the top-right of this repo.

## Versioning

The schema follows a separate version track from team definition versions:

- `https://schema.openenvelope.org/team/v1.json` — current stable
- `https://schema.openenvelope.org/team/v2.json` — future major (not yet released)

Within a major version (v1), Envelope commits to backwards compatibility: no field removals, no type changes, additions only. See the full [schema versioning policy](https://openenvelope.org/docs/schema/versioning-policy).

## What counts as a breaking change

A new major version is required when:

- A field that was previously valid is removed
- A field's type changes
- A previously optional field becomes required
- A previously valid enum value is removed

Additions (new optional fields, new enum values) are non-breaking and ship as minor releases within v1.

## Full documentation

- [Schema reference](https://openenvelope.org/docs/schema) — all fields, types, constraints, and examples
- [Schema versioning policy](https://openenvelope.org/docs/schema/versioning-policy) — lifecycle, deprecation, platform obligations
- [Ecosystem overview](https://openenvelope.org/docs/ecosystem) — builder/deployer model, CLI, npm packages

## License

Apache 2.0. See [LICENSE](LICENSE).

## Community

Questions, feedback, and schema discussion happen in the [Envelope Discord](https://discord.gg/Ubzq5FUXK4). The `#schema` channel is the right place for spec questions.

## Contact

Questions about the schema spec: open an issue or join the [Discord](https://discord.gg/Ubzq5FUXK4). Security disclosures: security@openenvelope.org.
