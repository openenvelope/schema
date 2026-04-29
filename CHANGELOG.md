# Changelog

All schema changes are documented here. Tags: `added`, `changed`, `deprecated`, `removed`, `fixed`, `security`.

---

## v1.0.0 — 2026-04-28

Initial public release.

**Schema:** `https://schema.openenvelope.org/team/v1.json`

**Added:**

- Top-level team fields: `$schema`, `name`, `slug`, `version`, `description`, `visibility`, `agents` (required); `category`, `tags`, `pricing`, `forkable`, `forkedFrom`, `timeout`, `readme`, `icon`, `inputs`, `outputs`, `requiredSecrets`, `requiredVariables`, `changelog` (optional)
- `agents` array with full `AgentDefinition`: `key`, `name`, `title`, `role` (required); `adapterType`, `reportsToKey`, `capabilities`, `prompt`, `model`, `modelConfig`, `allowedHosts`, `accessPolicy`, `metadata` (optional)
- `ModelConfig` object: `provider`, `model` (required); `temperature`, `maxTokens`, `timeoutMs` (optional)
- `AccessPolicy` object with ordered `rules` array: per-rule `host`, `methods`, `pathPrefix`, `action`, `reason`; `action` values: `allow`, `deny`, `require_approval` (forward-compatible, treated as `deny` in v1)
- `gates` array with `HumanGate`: `name`, `type`, `afterStep`, `triggersStep`, `fields`, `trigger`, `onReject` (required); `thresholdCount`, `recordActions`, `timeout` (optional)
- `pipeline` array with `PipelineStep`: `key`, `agentKey` (required); `label`, `dependsOn` (optional)
- `Pricing` with `model` values: `free`, `per_run`, `per_k_tokens`, `subscription` (subscription planned — not yet available)
- `ForkedFrom` attribution object for forked teams
- `TeamTimeout` with `runMs` and `agentMs`
- Category enum: 15 values (`customer-support`, `sales`, `marketing`, `finance`, `hr`, `devops`, `engineering`, `data-analysis`, `legal`, `research`, `content`, `product`, `security`, `operations`, `other`)
- Adapter enum: `http`, `claude_local`, `codex_local`, `gemini_local`, `opencode_local`, `cursor_local`
