# EstateBolt AI — curated open-source modules (17 October 2026)

> Separate research branch. The original `main` branch of `free-claude-code` is untouched. These are **upstream links** and a selection blueprint, not vendored third-party code or included model weights. EstateBolt is independent and not endorsed by the upstream authors.

## Recommended stack

| Layer | Upstream repository | Status | License considerations |
|---|---|---|---|
| AI coding agent | https://github.com/anomalyco/opencode | **Preferred** | MIT; needs isolated agent runner |
| Agent orchestration | https://github.com/OpenHands/OpenHands | **Preferred alternative** | MIT; isolate access to filesystem |
| Browser site builder | https://github.com/stackblitz-labs/bolt.diy | Optional | MIT sources **but WebContainers API commercial license may be required** |
| AI pair programming | https://github.com/Aider-AI/aider | Optional | Verify release license |
| IDE agent | https://github.com/continuedev/continue | Optional | Verify release license |
| Image/video engine | https://github.com/Comfy-Org/ComfyUI | **Preferred** | GPL-3.0; keep as independent API service |
| Image UI alternative | https://github.com/invoke-ai/InvokeAI | Optional | Multiple licenses; review components |
| ComfyUI nodes manager | https://github.com/Comfy-Org/ComfyUI-Manager | Optional | Audit third-party nodes |
| Video generation | https://github.com/Wan-Video/Wan2.2 | **Preferred model family** | Apache-2.0 with usage terms; GPU required |
| Video alternative | https://github.com/Lightricks/LTX-Video | Optional | Model-specific licensing may differ from source |
| Model hosting | https://github.com/ollama/ollama | **Preferred** | MIT program; model weights separately licensed |
| Low-level inference | https://github.com/ggml-org/llama.cpp | Optional | MIT; technical integration |
| Sandbox | https://github.com/e2b-dev/E2B | **Preferred candidate** | Apache-2.0; hosted usage may cost |
| Browser testing | https://github.com/microsoft/playwright | Recommended | Apache-2.0 |
| Chat UI reference | https://github.com/open-webui/open-webui | Reference only | Custom Open WebUI License and branding requirement |

## Do not choose as default

- https://github.com/daytonaio/daytona — the repository states maintenance of its open core stopped in June 2026.
- Anonymous unreviewed plugin repositories, unmaintained forks or checkpoint downloads with unclear provenance.
- Any model labeled "uncensored" as a replacement for authentication, audit logs or content-law compliance.

## Android model

Chrome on Android is a **client**. Heavy local coding models and image/video inference must execute on a machine with suitable compute resources (server or desktop GPU). Unlimited free hosted compute is not available merely because code is open source.

## Project files

The separate EstateBolt Super v2 source package contains the working frontend and API adapters (OpenRouter, Gemini, Ollama, ComfyUI images). This research branch deliberately does not copy unrelated upstream code or claim that OpenCode/OpenHands, Wan video or GitHub OAuth integration already works.

Read `ARCHITECTURE.md` for the implementation sequence and `modules.json` for a machine-readable catalog.