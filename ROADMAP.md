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
| Multi-Provider MCP Server | 📋 | MCP · Claude/GPT/Gemini adapter | MCP in practice + provider-agnostic architecture |
| RAG Knowledge Assistant | 📋 | Embeddings · vector store · FastAPI | End-to-end RAG |
| **AI Data & Evaluation** — Rubric-Based Fine-Tuning Pipeline | 📋 | Multi-criteria rubrics · preference data · fine-tuning | see detail below |
| Price Prediction with ML | 📋 | scikit-learn · neural network (PyTorch/Keras) | Machine Learning, Deep Learning, neural networks, predictive modeling |

**Detail — AI Data & Evaluation:**

1. A set of LLM outputs for a fixed task (e.g., summarization, code review, or a support reply)
2. A documented multi-criteria rubric (e.g., factual correctness, completeness, format adherence, tone) with an objective scale and definition per level — no "1-to-5 score" without a written criterion
3. A scoring harness applying the rubric to the outputs, producing preference data (A/B pairs with a per-criterion justification)
4. A consistency check against a golden set
5. Using the preference data to guide a real fine-tuning run, even on a small model — the pipeline matters more than the model size
6. A README explaining the rubric-design methodology — that part is what shows rigor, not just the code

## Automation, Scraping & Bots

| Project | Status | Stack | What it demonstrates |
|---|---|---|---|
| [Web Scraper Toolkit](https://github.com/LacerdaTraderCode/web-scraper-toolkit) | ✅ | BeautifulSoup · Selenium · Playwright | Practical comparison of the three approaches |
| [Telegram Crypto Alert Bot](https://github.com/LacerdaTraderCode/telegram-crypto-alert-bot) | ✅ | python-telegram-bot · Binance API · asyncio | Fully async architecture |
| [Discord Moderation Bot](https://github.com/LacerdaTraderCode/discord-moderation-bot) | ✅ | discord.py 2.x · SQLAlchemy | Slash commands, anti-spam, cogs |
| WhatsApp Sticker Converter | 🚧 | FastAPI · React/Vite · JWT | Real full-stack work, outside the trading domain |
| n8n + Make Automation Suite | 📋 | n8n · Make · Flask webhook receiver | Closes n8n, Make, and Flask in one project |

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
- [ ] n8n + Make Automation Suite

### Wave 2 — Applied AI
- [ ] Multi-Provider MCP Server
- [ ] RAG Knowledge Assistant
- [ ] AI Data & Evaluation — Rubric-Based Fine-Tuning Pipeline

### Wave 3 — Trading & Quant
- [ ] Quant Strategy Simulator
- [ ] Price Prediction with ML
- [ ] MQL5 EA + Python analysis

### Wave 4 — Frontend, Mobile & Infra
- [ ] Next.js Dashboard
- [ ] Flutter App
- [ ] Wallet & Ledger System
- [ ] Reference Architecture (Docker + K8s + CI/CD)
