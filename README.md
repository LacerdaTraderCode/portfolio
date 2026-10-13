<div align="center">

# 🎯 Portfolio — Wagner Lacerda

### Senior Software Engineer | Python • Backend • AI Apps • Automation • Bots • Systems

</div>

12+ years in IT, independent since 2019. APIs, data pipelines, automation, and applied
LLM/AI work — see the [full profile](https://github.com/LacerdaTraderCode) for
background, full stack, and contact.

> 💡 **Most of my professional projects are private due to client NDAs.** The 16 public
> repositories below demonstrate the technologies I use in practice, grouped by area.
> Click a group to expand it.

---

## 🧠 Applied AI

<details>
<summary><b>4 projects</b> — Model Context Protocol, RAG, LLM evaluation, and ML prediction</summary>

<br>

### [Multi-Provider MCP Server](https://github.com/LacerdaTraderCode/mcp-multi-llm-server)
Model Context Protocol server that queries and compares Claude, GPT, and Gemini
side by side through a single interface.

**Stack:** `MCP` `Claude / GPT / Gemini adapters` `httpx`

- Adapter-per-vendor design — adding a new provider means adding one file, not touching existing ones
- Providers are opt-in based on which API keys are configured, with no hard failure when one is missing
- Comparison logic is decoupled from the MCP transport layer, so it's testable on its own and via a real MCP session

---

### [RAG Knowledge Assistant](https://github.com/LacerdaTraderCode/rag-knowledge-assistant)
End-to-end retrieval-augmented generation pipeline that answers questions grounded
in a document set, with citations back to the source chunks.

**Stack:** `TF-IDF retrieval` `FastAPI` `Claude`

- TF-IDF retrieval chosen deliberately over embeddings — runs fully offline, deterministic, no API key required just to test retrieval quality
- Every generated answer returns alongside the exact chunks it was grounded in, not just a confident-sounding response

---

### [AI Data & Evaluation](https://github.com/LacerdaTraderCode/ai-data-evaluation)
Rubric-based evaluation pipeline for LLM outputs, producing labeled data usable
for fine-tuning.

**Stack:** `Anchored rubrics` `LLM-as-judge` `Preference data (DPO-shaped)`

- A golden-set agreement check validates the LLM judge against human-labeled examples before trusting its scores
- Score gaps between ranked outputs are converted directly into DPO-style preference pairs

---

### [Price Prediction ML](https://github.com/LacerdaTraderCode/price-prediction-ml)
Classification models predicting short-term price direction, benchmarked against
a naive baseline.

**Stack:** `scikit-learn` `Random Forest` `MLP`

- Chronological train/test split and lookahead-free features — avoids the temporal leakage that quietly inflates backtest accuracy
- Every model is compared against a baseline predictor, so "better than chance" is actually demonstrated, not assumed

</details>

## 🔧 Backend, Data & Architecture

<details>
<summary><b>3 projects</b> — REST APIs and high-performance data pipelines</summary>

<br>

### [FastAPI REST Boilerplate](https://github.com/LacerdaTraderCode/fastapi-rest-boilerplate)
Production-ready REST API template with JWT authentication and full CRUD,
intended as a real starting point, not a toy example.

**Stack:** `FastAPI` `SQLAlchemy` `JWT` `Pydantic`

- JWT auth with bcrypt password hashing and refresh-token handling built in, not bolted on later
- Interactive Swagger/OpenAPI docs generated automatically from the Pydantic schemas

---

### [Django Ninja + MongoDB API](https://github.com/LacerdaTraderCode/django-ninja-mongo-api)
Async REST API combining Django Ninja's typed routing with MongoDB as the
primary store.

**Stack:** `Django Ninja` `MongoDB` `Motor` `JWT`

- Fully async data access via Motor, paired with Django Ninja's type-hinted request/response validation
- Argon2 password hashing, stronger by default than the more common bcrypt/PBKDF2 choices

---

### [Data Pipeline — Polars & DuckDB](https://github.com/LacerdaTraderCode/data-pipeline-polars-duckdb)
Modern ETL pipeline built for throughput, moving data through Parquet and SQL
without a Pandas bottleneck.

**Stack:** `Polars` `DuckDB` `Parquet`

- Benchmarked at 10-100x faster than an equivalent Pandas pipeline, with the benchmark included in the repo, not just claimed
- DuckDB used for the SQL-shaped transforms, Polars for the rest — each tool used where it's actually faster

</details>

## 🤖 Automation, Scraping & Bots

<details>
<summary><b>4 projects</b> — scraping, Telegram/Discord bots, and no-code integration</summary>

<br>

### [Web Scraper Toolkit](https://github.com/LacerdaTraderCode/web-scraper-toolkit)
Complete scraping toolkit covering three different extraction strategies for
three different kinds of target.

**Stack:** `Selenium` `Playwright` `BeautifulSoup` `Polars`

- Three scrapers, not one — BeautifulSoup for static HTML, Playwright/Selenium for JS-rendered pages, picked per target instead of forcing one tool everywhere
- Built-in rate-limiting to avoid hammering target sites, with results exported to Parquet via Polars

---

### [Telegram Crypto Alert Bot](https://github.com/LacerdaTraderCode/telegram-crypto-alert-bot)
Real-time price-alert bot that watches the Binance API and notifies users the
moment a threshold is crossed.

**Stack:** `python-telegram-bot` `Binance API` `asyncio` `SQLAlchemy`

- Fully async with `asyncio` + `aiohttp`, so price polling never blocks the bot's command handling
- Per-user alert thresholds persisted via SQLAlchemy, scheduled with APScheduler instead of a naive sleep loop

---

### [Discord Moderation Bot](https://github.com/LacerdaTraderCode/discord-moderation-bot)
Moderation bot built around Discord's modern slash-command interface, with
persisted infractions.

**Stack:** `discord.py` `SQLAlchemy` `asyncio`

- Slash commands throughout, not legacy prefix commands — matches how Discord actually expects bots to behave today
- Moderation actions and infractions persisted to a database, so history survives a bot restart

---

### [n8n & Make Automation Suite](https://github.com/LacerdaTraderCode/n8n-make-automation-suite)
Webhook-driven automation suite connecting no-code platforms (n8n, Make) to a
custom Flask backend for logic that doesn't fit visual workflows.

**Stack:** `Flask` `n8n` `Make` `Webhooks`

- Used where it genuinely fits: no-code platforms handle orchestration, Flask handles the logic (e.g., lead scoring) that needs real code
- Integrates with Telegram and Slack as delivery channels for automated workflow outputs

</details>

## 📈 Trading & Quant

<details>
<summary><b>3 projects</b> — technical analysis, strategy simulation, and EA trade analysis</summary>

<br>

### [Streamlit Finance Dashboard](https://github.com/LacerdaTraderCode/streamlit-finance-dashboard)
Interactive dashboard with technical indicators for market analysis, built for
quick visual read of price action.

**Stack:** `Streamlit` `Plotly` `yfinance`

- SMA, EMA, RSI, MACD, and Bollinger Bands, plotted on interactive Plotly candlestick charts
- Display and analysis only, by design — no order execution path, so it can't be mistaken for a live trading tool

---

### [Quant Strategy Simulator](https://github.com/LacerdaTraderCode/quant-strategy-simulator)
Backtester comparing money-management strategies across thousands of simulated
trade sequences.

**Stack:** `Monte Carlo simulation` `DuckDB` `Kelly Criterion`

- Fixed, Martingale, D'Alembert, Fibonacci, and Kelly Criterion compared on **ruin rate**, not just average return — the metric that actually matters for risk of blowing an account
- Hundreds of Monte Carlo trials aggregated and queried via DuckDB SQL

---

### [MQL5 EA + Trade Analysis](https://github.com/LacerdaTraderCode/mql5-ea-analysis)
A real MetaTrader 5 Expert Advisor paired with a Python/Polars pipeline that
analyzes its exported trade log.

**Stack:** `MQL5` `Polars` `MetaTrader 5`

- A complete, functioning EA with percent-risk position sizing, not a stripped-down demo
- Win rate, profit factor, expectancy, and max drawdown computed directly from the EA's own trade log

</details>

## ⚙️ DevOps, Infra & Security

<details>
<summary><b>2 projects</b> — automation scripts and a multi-platform security scanner</summary>

<br>

### [Security Scanner](https://github.com/LacerdaTraderCode/security-scanner)
Multi-platform security analysis platform (Web, Mobile, Desktop) combining
SAST, SCA, secret detection, and authorized DAST, with AI-generated fix prompts.

**Stack:** `Next.js` `Semgrep` `Gitleaks` `OSV-Scanner` `Nuclei` `Claude API`

- Orchestrates Semgrep, Gitleaks, OSV-Scanner/Trivy, MobSF, Nuclei, and Checkov behind one pipeline, instead of running each tool by hand
- Every finding gets an automatically generated, ready-to-paste Claude Code fix prompt with the exact file, line, and expected fix
- Active pentest (Nuclei) requires explicit, audited authorization confirmation on two independent layers before it runs against any URL — never runs against a target without consent

---

### [Python Automation Scripts](https://github.com/LacerdaTraderCode/python-automation-scripts)
A collection of 8 standalone automation scripts for everyday system and file
tasks.

**Stack:** `Python` `pathlib` `psutil`

- Covers file organizing, backups, duplicate finding, log analysis, Excel handling, email automation, and system monitoring
- Each script is self-contained and runnable on its own — no shared framework required to use just one of them

</details>

---

<details>
<summary><b>🛠️ Full Tech Stack</b></summary>

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat-square&logo=fastapi)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask)
![Django Ninja](https://img.shields.io/badge/Django_Ninja-092E20?style=flat-square&logo=django&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=sqlite&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Polars](https://img.shields.io/badge/Polars-CD792C?style=flat-square&logo=polars&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat-square&logo=duckdb&logoColor=black)
![Claude](https://img.shields.io/badge/Claude-D97757?style=flat-square&logo=anthropic&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)

See the [profile README](https://github.com/LacerdaTraderCode) for the complete,
categorized stack.

</details>

---

<div align="center">

📧 [lacerdatradercode@outlook.com](mailto:lacerdatradercode@outlook.com) ·
💼 [LinkedIn](https://www.linkedin.com/in/wagner-lacerda-da-silva-958b9481) ·
🐙 [Profile](https://github.com/LacerdaTraderCode)

</div>
