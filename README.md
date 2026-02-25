# VerifAIble

**Make every bit of information verifiable to everyone.**

[中文版](README_zh.md) · [Website](https://ai.verifaible.space/)

![Release](https://img.shields.io/github/v/release/ChizhongWang/OpenVerifAIble?label=release)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Android%20%7C%20Web-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## What is VerifAIble?

VerifAIble is an AI-powered content creation platform where **every AI response is backed by verifiable evidence**. Unlike traditional AI chatbots that generate plausible but unverifiable text, VerifAIble's Agent system actively searches the web, collects evidence, and creates citations that link directly to highlighted source material — making AI-generated content auditable and trustworthy.

🌐 Try it at [ai.verifaible.space](https://ai.verifaible.space/)

---

## Key Features

### Agent System & Tool Use

A self-developed Agent SDK (`verifaible-agent-sdk`) implements a complete **Tool Loop**: model reasoning → tool calls → result feedback → continued reasoning. The Agent is equipped with **18 built-in tools** (file I/O, shell execution, web search & analysis, citation creation, image generation, etc.) with progressive tool discovery and sub-agent orchestration.

### Multi-Provider Abstraction

Unified routing layer via OpenRouter connecting **7 providers and 12+ models**: OpenAI (GPT-5.1/5.2), Google Gemini (3-Pro/3-Flash), DeepSeek (Chat/R1), Anthropic (Claude Sonnet 4.6), MiniMax (M2.5), Zhipu (GLM-5), and Moonshot (Kimi-K2.5). Hot-swappable model switching with streaming SSE responses.

### Verifiable Citations

The **VerifAIble Link** system — a custom URL hash protocol (`#verifaible:anchor=...&text=...&id=...&claim=...&evidence_type=...`) — enables precise playback and source tracing for **7 evidence types**: webpage, text, table, PDF, video, document, and image. Features include:
- **Text**: DOM traversal + anchor/context dual-layer highlighting + fuzzy date matching
- **Table**: Row-column crosshair positioning with rowspan/colspan support
- **PDF**: Redirect to built-in PDF.js viewer with page + anchor navigation
- **Video**: YouTube timestamp auto-jump with player render detection
- **Dynamic pages**: Action Steps Replay — record and replay user interaction sequences (click/input/scroll/JS execution)
- **Fault tolerance**: 6-level delayed retry (500ms → 5s) for AJAX-loaded content

### Microservice Architecture

6 independent services powering the platform:

| Service | Tech | Responsibility |
|---------|------|---------------|
| API Gateway | FastAPI | Request routing, CORS, auth middleware, rate limiting |
| Auth Service | FastAPI | Google OAuth 2.0, email verification (Resend), JWT |
| Chat Service | FastAPI | Multi-model LLM dialogue, SSE streaming, citation mode |
| Agent Service | FastAPI | AI agent execution, tool loop, multi-turn conversation |
| Evidence Service | Playwright | Web screenshot capture, evidence storage & indexing, public sharing |
| LLM Gateway | — | Unified LLM API routing |

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        Client Layer                             │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────────────┐ │
│  │   Electron   │  │   Android    │  │     Web Browser        │ │
│  │  (Vue 3 +    │  │  (Capacitor) │  │  (ai.verifaible.space) │ │
│  │   Pinia)     │  │              │  │                        │ │
│  └──────┬───────┘  └──────┬───────┘  └───────────┬────────────┘ │
└─────────┼─────────────────┼──────────────────────┼──────────────┘
          │                 │                      │
          └─────────────────┼──────────────────────┘
                            │ HTTPS / SSE
          ┌─────────────────▼──────────────────┐
          │          API Gateway (:8000)        │
          │     FastAPI · CORS · JWT Auth       │
          └──┬──────┬──────────┬───────────┬───┘
             │      │          │           │
     ┌───────▼──┐ ┌─▼────────┐│┌──────────▼────────┐
     │   Auth   │ │   Chat   │││   Agent Service   │
     │  (:8001) │ │  (:8002) │││     (:8003)       │
     │ OAuth+JWT│ │ SSE+LLM  │││ Tool Loop · 18    │
     └──────────┘ └──────────┘││ tools · Sub-agent  │
                              │└────────────────────┘
                   ┌──────────▼────────┐
                   │ Evidence Service  │
                   │   Playwright      │
                   │ Screenshot+Share  │
                   └───────────────────┘
                              │
          ┌───────────────────▼───────────────────┐
          │           LLM Gateway                 │
          │  OpenRouter → 7 Providers · 12 Models │
          └───────────────────────────────────────┘
                              │
          ┌───────────────────▼───────────────────┐
          │         PostgreSQL 15 + Redis 7        │
          └────────────────────────────────────────┘
```

---

## Download

### macOS (Apple Silicon)
- [VerifAIble-0.0.0-arm64.dmg](https://github.com/ChizhongWang/OpenVerifAIble/releases/download/v0.0.0/VerifAIble-0.0.0-arm64.dmg)

### Windows
Coming soon

### Web
- [ai.verifaible.space](https://ai.verifaible.space/)

> **Note:** This app is not code-signed. On first launch, you may need to allow it in **System Preferences > Security & Privacy**.

---

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | Vue 3, TypeScript, Pinia, Electron, Chromium (built-in browser), Tailwind CSS |
| Backend | FastAPI, Python 3.11+, SQLAlchemy, Pydantic |
| Database | PostgreSQL 15, Redis 7 |
| LLM | OpenAI API, Gemini API, DeepSeek API, Anthropic Claude API, OpenRouter |
| DevOps | Docker, Docker Compose, PNPM, Poetry |
| Tools | Playwright, Resend, JWT, Capacitor (Android) |

---

## Related Projects

| Project | Description |
|---------|-------------|
| [verifaible-bench](https://github.com/ChizhongWang/verifaible-bench) | Benchmark framework for evaluating LLM agents on verifiable evidence collection |
| [verifaible-model](https://github.com/ChizhongWang/verifaible-model) | SFT fine-tuning for evidence collection capabilities |

---

## License

MIT

---

© 2026 VerifAIble
