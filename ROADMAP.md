# 🗺️ Technical Portfolio Roadmap

> Expansion plan for the public portfolio at [github.com/LacerdaTraderCode](https://github.com/LacerdaTraderCode). Covers the full stack — languages, data, AI, automation, DevOps, and trading — with no single job posting in mind.

## Legend

- ✅ Published
- 🚧 Exists, not yet published/polished
- 📋 Planned
- 🔀 Variation of an existing project (same problem, different stack)

---

## Backend, Data & Architecture

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [FastAPI REST Boilerplate](https://github.com/LacerdaTraderCode/fastapi-rest-boilerplate) | ✅ | FastAPI · SQLAlchemy · JWT · Pydantic · PostgreSQL | Production-ready REST API, JWT auth, automatic Swagger docs |
| [Django Ninja + MongoDB API](https://github.com/LacerdaTraderCode/django-ninja-mongo-api) | ✅ | Django Ninja · MongoDB (Motor) · JWT · argon2 | Same problem as the boilerplate above, second stack — closes the NoSQL gap |
| Wallet & Ledger System | 📋 | PostgreSQL · relational modeling · double-entry accounting | Real relational modeling, not a simple CRUD |
| [Data Pipeline Polars & DuckDB](https://github.com/LacerdaTraderCode/data-pipeline-polars-duckdb) | ✅ | Polars · DuckDB · Parquet · PyArrow | Modern ETL, 10-100x faster than Pandas, benchmark included |

## Applied AI

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [Multi-Provider MCP Server](https://github.com/LacerdaTraderCode/mcp-multi-llm-server) | ✅ | MCP (official SDK) · Claude/GPT/Gemini adapters · httpx2 | MCP in practice + provider-agnostic architecture |
| [RAG Knowledge Assistant](https://github.com/LacerdaTraderCode/rag-knowledge-assistant) | ✅ | TF-IDF retrieval · FastAPI · Claude | End-to-end RAG with cited, grounded answers |
| [AI Data & Evaluation](https://github.com/LacerdaTraderCode/ai-data-evaluation) | ✅ | Anchored rubrics · LLM-as-judge · preference data | Rubric design, golden-set agreement checking, DPO-shaped preference data |
| Price Prediction with ML | 📋 | scikit-learn · neural network (PyTorch/Keras) | Machine Learning, Deep Learning, neural networks, predictive modeling |

## Automation, Scraping & Bots

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [Web Scraper Toolkit](https://github.com/LacerdaTraderCode/web-scraper-toolkit) | ✅ | BeautifulSoup · Selenium · Playwright | Practical comparison of the three approaches |
| [Telegram Crypto Alert Bot](https://github.com/LacerdaTraderCode/telegram-crypto-alert-bot) | ✅ | python-telegram-bot · Binance API · asyncio | Fully async architecture |
| [Discord Moderation Bot](https://github.com/LacerdaTraderCode/discord-moderation-bot) | ✅ | discord.py 2.x · SQLAlchemy | Slash commands, anti-spam, cogs |
| WhatsApp Sticker Converter | 🚧 | FastAPI · React/Vite · JWT | Real full-stack work, outside the trading domain |
| [n8n + Make Automation Suite](https://github.com/LacerdaTraderCode/n8n-make-automation-suite) | ✅ | n8n · Make · Flask webhook receiver | Closes n8n, Make, and Flask in one project |

## Frontend & Mobile

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| Next.js Dashboard (SSR) | 📋 | Next.js · TypeScript · React | React/Vite already exists in the sticker converter — this closes Next.js/SSR and TS |
| Flutter App | 📋 | Flutter · Dart | Mobile — currently zero coverage |

## Trading & Quant

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [Streamlit Finance Dashboard](https://github.com/LacerdaTraderCode/streamlit-finance-dashboard) | ✅ | Streamlit · Plotly · yfinance | Display-only technical indicators |
| Quant Strategy Simulator | 📋 | Plain Python · Pytest · DuckDB | Generalized classic money-management strategies (backtest, not a live signal) |
| MQL5 EA + Python analysis | 📋 | MQL5 · Polars | A rare skill — zero coverage today |

## DevOps & Infra

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [Python Automation Scripts](https://github.com/LacerdaTraderCode/python-automation-scripts) | ✅ | pathlib · openpyxl · psutil · smtplib · hashlib | 8 IT utility scripts |
| Reference Architecture (Deploy) | 📋 | Docker · Kubernetes · GitHub Actions | Full pipeline: local compose → image → Helm/manifests → CI/CD, documented for AWS/GCP/OCI/Vercel |

> SAP, ServiceNow, Jira, and Active Directory are deliberately left out — already represented in the hub's "Professional Background" table; turning them into a repository would be decoration, not signal.

---

## Standard required in every repository (existing or new)

- Real tests with Pytest — no placeholders
- CI via GitHub Actions (lint + tests) on every PR
- README with purpose, stack, how to run, and architecture decisions
- Variable and function names tied to the domain — never generic
- Comments only when they explain the *why*, never the *what*
- One module, one responsibility
- All repository content — code, comments, documentation, and usage examples — in English

---

## Execution waves

The order is purely technical — whatever unblocks or speeds up the rest comes first, with no priority given to any single job posting.

### Wave 1 — Foundation
- [x] Django Ninja + MongoDB API
- [ ] Publish/polish WhatsApp Sticker Converter
- [x] n8n + Make Automation Suite

### Wave 2 — Applied AI ✅ complete
- [x] Multi-Provider MCP Server
- [x] RAG Knowledge Assistant
- [x] AI Data & Evaluation — Rubric-Based Fine-Tuning Pipeline

### Wave 3 — Trading & Quant
- [ ] Quant Strategy Simulator
- [ ] Price Prediction with ML
- [ ] MQL5 EA + Python analysis

### Wave 4 — Frontend, Mobile & Infra
- [ ] Next.js Dashboard
- [ ] Flutter App
- [ ] Wallet & Ledger System
- [ ] Reference Architecture (Docker + K8s + CI/CD)
