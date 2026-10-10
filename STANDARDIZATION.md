# Portfolio Standardization Tracker

Tracks the effort to bring the seven public portfolio repositories to the same professional standard as the newer ones. Reference repository: [`rag-knowledge-assistant`](https://github.com/LacerdaTraderCode/rag-knowledge-assistant).

_Last updated: 2026-10-10_

## Target standard

Every repository must have:

- `.github/workflows/ci.yml`: Python 3.12, `ruff check`, `ruff format --check`, `pytest -v`, on push and pull request to `main`
- `pyproject.toml` with ruff settings (`line-length = 100`, rules `E`, `F`, `I`, `UP`, `RUF`)
- `pytest.ini` and a `tests/` package exercising every module
- `requirements-dev.txt` with pinned `pytest` and `ruff` (plus `pytest-asyncio` or `httpx` when needed)
- `.env.example` when the project reads environment variables
- README with a CI badge, an accurate project structure and a development section
- English-only code, messages and docs; no redundant comments or docstrings
- GitHub "About" description reflecting the project

Delivery rules: one branch and one pull request per repository, merged only after CI is green. The old `ci/github-actions` pull request (#2) is closed as superseded.

## Status

| Repository | Pull request | CI | Status |
|---|---|---|---|
| [fastapi-rest-boilerplate](https://github.com/LacerdaTraderCode/fastapi-rest-boilerplate) | [#3](https://github.com/LacerdaTraderCode/fastapi-rest-boilerplate/pull/3) | Green | Merged |
| [telegram-crypto-alert-bot](https://github.com/LacerdaTraderCode/telegram-crypto-alert-bot) | [#3](https://github.com/LacerdaTraderCode/telegram-crypto-alert-bot/pull/3) | Green | Merged |
| [web-scraper-toolkit](https://github.com/LacerdaTraderCode/web-scraper-toolkit) | [#3](https://github.com/LacerdaTraderCode/web-scraper-toolkit/pull/3) | Green | Merged |
| [data-pipeline-polars-duckdb](https://github.com/LacerdaTraderCode/data-pipeline-polars-duckdb) | [#3](https://github.com/LacerdaTraderCode/data-pipeline-polars-duckdb/pull/3) | Green | Merged |
| [streamlit-finance-dashboard](https://github.com/LacerdaTraderCode/streamlit-finance-dashboard) | [#3](https://github.com/LacerdaTraderCode/streamlit-finance-dashboard/pull/3) | Green | Merged |
| [python-automation-scripts](https://github.com/LacerdaTraderCode/python-automation-scripts) | - | - | Pending |
| [discord-moderation-bot](https://github.com/LacerdaTraderCode/discord-moderation-bot) | - | - | Pending |

GitHub "About" descriptions are updated on all seven repositories.

## Changes and fixes by repository

### fastapi-rest-boilerplate
- Added missing `email-validator` and pinned `bcrypt==4.0.1` for passlib compatibility
- Extracted the repeated owner lookup in the items router
- Tests: auth, items CRUD, pagination, ownership isolation, users, health (in-memory SQLite)
- Added `.env.example` referenced by the README

### telegram-crypto-alert-bot
- Fixed `import asyncio` placed at the bottom of `binance_client.py`
- Replaced `== True` comparisons, removed placeholder-less f-strings, retained the background monitor task reference
- Extracted `build_application` and `is_triggered` for testability
- Tests: handlers, monitor, Binance client (fake HTTP session), persistence, bootstrap

### web-scraper-toolkit
- Selenium scraper accepts an injected driver; Playwright scraper always closes the browser
- `fetch` retries now re-raise the original HTTP error
- Rate limiter uses a monotonic clock; prints replaced by logging
- Examples run as modules (`python -m examples.<name>`)
- Tests: all three scrapers (mocked), exporters, rate limiter

### data-pipeline-polars-duckdb
- `read_excel` uses the `openpyxl` engine already in requirements (the default engine needed an uninstalled package)
- Fixed `monthly_trend`, which failed when the data already had a `month` column
- Parquet path is escaped before interpolation into SQL
- Tests: extract, transform, load, DuckDB analysis, example scripts end to end

## Open items

1. **Topics and homepage:** not settable with the current tooling. Add manually under each repository's About settings (suggested: `fastapi`, `jwt`, `sqlalchemy`, `telegram-bot`, `binance`, `web-scraping`, `playwright`, `polars`, `duckdb`, `etl`, `streamlit`, `plotly`, `discord-py`).
2. **telegram-crypto-alert-bot README** claims automatic rate limiting that the code does not implement. Remove the claim or implement it.
3. **telegram-crypto-alert-bot** lists `apscheduler` in `requirements.txt` but never uses it.
4. **web-scraper-toolkit README** performance table has unverified timings.
5. **data-pipeline-polars-duckdb README** lists "joins" as a feature that does not exist and has an unverified comparison table.
6. **Stale branches:** `ci/github-actions` still exists in all merged repositories. Delete after confirmation.

## Remaining work

1. **streamlit-finance-dashboard**: extract chart building from the monolithic `app.py` into a testable module, translate the UI, test indicators (SMA, EMA, RSI, MACD, Bollinger), metrics, mocked `yfinance` and the app via `streamlit.testing.v1.AppTest`.
2. **python-automation-scripts**: tests for the eight scripts using temporary directories; mock SMTP and system metrics.
3. **discord-moderation-bot**: tests for cogs and database with mocked `discord.py` objects.
4. Close out the open items above and delete stale branches.
