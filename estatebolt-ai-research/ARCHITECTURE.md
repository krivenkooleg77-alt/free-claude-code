# EstateBolt AI — architecture and implementation gates

## Current usable baseline

- Single-operator responsive AI HTML/CSS/JS editor with local browser projects, ZIP import/export and sandboxed preview.
- HTTP backend with OpenRouter / Gemini / self-hosted Ollama provider integration.
- Private ComfyUI image API adapter with default checkpoint workflow; needs external running ComfyUI and installed checkpoint.
- Video UI/API scaffold only. A compatible ComfyUI video workflow and video checkpoint have **not** been installed.
- Catalog stored in a standalone JSON file; no third-party code vendored.

## Intended production architecture

```
Android Chrome
 -> Cloudflare Access / auth gateway -> HTTPS
 -> EstateBolt API (RBAC, audit logs, rate limits)
     -> LLM gateway -> Ollama and/or external providers
     -> agent worker -> OpenCode/OpenHands -> isolated E2B microVM
     -> media queue -> private ComfyUI GPU worker -> image/video artifacts to S3
     -> GitHub App (scoped OAuth) -> PR / review / CI pipeline
     -> PostgreSQL (projects, jobs, roles, file metadata)
 -> preview deploy -> quality checks -> approval -> production deploy
```

## Gates before allowing external users

1. Agent actions only in sandbox. Never mount the Docker host socket into the public app.
2. Fine-grained GitHub authorization, one workspace scope, separate branches, diff/review before merge.
3. Media: job quotas, GPU billing, weight/model license checks, output retention and abuse controls.
4. Per-user API key vault, SSO, rate limiting, abuse reports, encryption, restore-tested backups.
5. Commercial terms: inspect release-specific licensing, particularly WebContainers, ComfyUI GPL, Open WebUI branding, and model weights.
6. Staging tests: unit/e2e, SAST, secret scanning, dependency audit, rollback.

## Build order

**P0:** protect platform, model configuration, private Ollama and ComfyUI image smoke tests.

**P1:** OpenCode/OpenHands worker, patch review, safe code execution, tests.

**P2:** Wan/LTX workflow on GPU, queue and media storage, video delivery.

**P3:** user accounts, plugins with permission manifest, per-workspace storage, GitHub PR workflow.

**P4:** use EstateBolt to generate the separate international real-estate marketplace; payments and crypto custody must be integrated only via a lawful regulated arrangement.

The project's goal is configurable choice of self-hosted models; no guarantee of illegal/unrestricted output or zero computing cost.