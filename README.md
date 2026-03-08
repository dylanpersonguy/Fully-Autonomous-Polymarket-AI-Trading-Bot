<div align="center">

# 📊 Polymarket Trading Bot — Automated AI Prediction Market Trading

### The Most Advanced Open-Source Polymarket Bot for Automated Prediction Market Trading

[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)](docker-compose.yml)

**A production-grade autonomous Polymarket trading bot that discovers prediction markets, researches evidence with web search, forecasts probabilities using a multi-model AI ensemble (GPT-4o, Claude, Gemini), and executes trades with 15+ independent risk checks and fractional Kelly position sizing.**

Paper trading by default. Three independent safety gates must be unlocked for live orders.

**Keywords:** Polymarket bot, Polymarket trading bot, prediction market bot, AI trading bot, automated trading, algorithmic trading, whale tracker, smart money, Kelly criterion, prediction market trading, Polymarket API, Polymarket CLOB

[Getting Started](#-getting-started) · [Dashboard](#-real-time-dashboard) · [Architecture](#%EF%B8%8F-architecture) · [Configuration](#%EF%B8%8F-configuration) · [Deployment](#-deployment)

</div>

---

## 🖥️ Real-Time Dashboard

A 9-tab glassmorphism dark-themed web dashboard provides complete visibility into every aspect of the trading system — from portfolio health to individual whale movements.

### Overview — Portfolio Health & Engine Status

![Dashboard Overview — Portfolio Cards, Equity Curve & Engine Controls](screenshots/overview-portfolio-cards.png)

The Overview tab is your command center. Six portfolio KPI cards display real-time **bankroll**, **total P&L** (realized + unrealized), **open position count**, **trade volume**, **average edge**, and **daily activity**. Below the cards, interactive charts render the **daily forecast & trade activity**, **edge vs. evidence quality scatter**, and a **market category distribution** doughnut. The full-width **equity curve** tracks cumulative portfolio value over time.

Engine status, drawdown heat level, Kelly multiplier, and the **kill switch** toggle are always visible — giving you one-click emergency halt capability.

![Dashboard Overview — Charts, Equity Curve & Market Regime](screenshots/overview-charts-activity.png)

The **Market Regime Detector** automatically classifies current conditions (Normal, Trending, Mean-Reverting, High Volatility, Low Activity) and adjusts position sizing multipliers in real time.

![Overview — Active Positions Table](screenshots/overview-positions-table.png)

The active positions table shows every open position with entry price, current price, stake, P&L ($/%),  price delta, and hold time. Click any row to expand a full position detail modal with microstructure data and trade history.

![Overview — Recent Forecasts](screenshots/overview-recent-forecasts.png)

Recent AI forecasts are displayed with the implied market probability vs. model probability, net edge, evidence quality score, source count, confidence level, and final trade/no-trade decision.

---

### Trading Engine — Pipeline Visualization & Cycle History

![Trading Engine — Controls & Pipeline](screenshots/trading-engine-controls.png)

The Trading tab provides **start/stop engine controls**, a live pipeline candidates log showing every market evaluated in the current cycle, and filter/search across all active positions. The summary strip shows total trades, win rate, P&L, take-profit/stop-loss hit counts, average hold time, and best/worst trades.

![Trading — Full Pipeline Visualization](screenshots/trading-pipeline-visualization.png)

The **pipeline visualization** renders the complete trading pipeline as a visual funnel — from market discovery through research, forecasting, risk checks, position sizing, and execution. Each stage shows pass/fail counts so you can see exactly where markets are filtered out.

![Trading — Cycle History & Trade Log](screenshots/trading-cycle-history.png)

Full **trade history** with status filters (Active, TP Hit, SL Hit, Resolved, Time Exit, Closed), P&L breakdown, close reason, duration, and paper/live mode indicator. Every trade is clickable for a detailed breakdown.

---

### Analytics — Performance Metrics & Strategy Leaderboard

![Analytics — KPIs & Performance Charts](screenshots/analytics-performance-metrics.png)

Six key performance indicators: **Win Rate** (with 7d/30d breakdown), **Sharpe Ratio** (with Sortino), **Profit Factor** (with avg win/loss), **Max Drawdown** (with Calmar ratio), **ROI** (with total staked), and **Current Streak** (with historical best/worst).

![Analytics — Category P&L & Calibration](screenshots/analytics-category-breakdown.png)

**Category P&L Breakdown** doughnut shows profit/loss distribution across market categories (Macro, Election, Corporate, Legal, Tech, etc.). The **Calibration Accuracy** chart plots forecast probability vs. actual resolution rate — the closer to the diagonal, the better calibrated the model.

![Analytics — Model Accuracy Comparison](screenshots/analytics-model-accuracy.png)

**Model Accuracy** comparison shows per-LLM Brier scores, enabling the adaptive weighting system to shift confidence toward the best-performing model for each category. The **Strategy Leaderboard** ranks categories by ROI, win rate, total P&L, and composite score.

---

### Whale Tracker — Smart Money Intelligence

![Whale Tracker — Conviction Signals & Smart Money Index](screenshots/whale-tracker-signals.png)

The **Smart Money Terminal** tracks top Polymarket traders in real time. The Smart Money Index (SMI) gauge provides a 0–100 bullish/bearish reading based on aggregate whale positioning. **Conviction signals** combine whale count × dollar size into actionable trade signals with strength indicators (Strong/Moderate).

The **7-phase liquid scanner pipeline** automatically discovers, analyzes, and scores whale wallets: Leaderboard → Markets → Global Trades → Market Trades → Ranking → Analysis → Score & Save.

![Whale Tracker — Wallet Leaderboard & Activity](screenshots/whale-tracker-wallets.png)

The **Whale Leaderboard** card view shows each tracked wallet's tier (👑 Legendary, 💎 Elite, ⭐ Pro, 🌱 Rising), P&L, win rate, conviction score, and recent activity. The **Activity Heatmap** visualizes 24-hour trading intensity. **High Consensus Alerts** fire when 3+ whales converge on the same position.

---

### Decision Intelligence — Full Audit Trail

![Decision Intel — Decision Center & Analytics](screenshots/decision-intel-log.png)

The **Decision Intelligence Center** provides complete transparency into every trading decision. Eight KPI cards show total decisions, trade rate, average DI score, average edge, evidence quality, pipeline completion rate, top category, and grade distribution. Charts break down decisions by type (Trade/No Trade/Skip/Error), grade (A–F), edge distribution, and category.

![Decision Intel — Detailed Decision Cards](screenshots/decision-intel-details.png)

Each decision expands into a full card showing the market question, decision type, grade, edge calculation, evidence quality, source breakdown, model reasoning, and the final pass/fail outcome for each of the 15 risk checks. Auto-generated insights surface patterns from decision history. **Missed Opportunities** highlight high-edge markets that were bypassed.

---

### Strategies & Wallets — Multi-Strategy Portfolio Management

![Strategies — Overview & Wallet Management](screenshots/strategies-overview.png)

Manage multiple **wallets** (paper and live) and **strategies** from a single interface. Create named wallets with custom colors, link strategies (AI Trading, Momentum, Mean Reversion, Whale Follow, Arbitrage, Custom), set risk profiles (Conservative/Moderate/Aggressive), and allocate capital across them. Summary KPIs show total balance, P&L, and activity across all wallets.

![Strategies — Backtesting & Performance](screenshots/strategies-backtesting.png)

Each strategy card shows its type, risk profile, linked wallets, allocation percentage, and live performance stats. Wallet performance details include dedicated equity curves and trade history per wallet.

---

### Trading Journal — Position Tracking & Risk Analytics

![Journal — Trade Log & Watchlist](screenshots/journal-trade-log.png)

The **Journal** tab combines portfolio VaR analytics (95%/99% VaR, Expected Loss), an **equity timeline** chart with 5-minute snapshots, a **market watchlist** for tracking specific condition IDs, and auto-generated **journal entries** when trades close — capturing outcome, lessons learned, and performance context.

---

### Admin Panel — System Health & Configuration

![Admin — Settings & Health Monitor](screenshots/admin-panel-settings.png)

The **Admin Panel** provides a system health score (0–100 with A–F grade), 8 system overview cards (uptime, engine cycles, DB size, API cost, configured keys, log size, memory usage, win/loss ratio), quick-action buttons (backup, vacuum, cache clear, log rotate, metric reset), and a full **risk monitor** with visual gauges for daily exposure, open positions, and evidence quality limits.

![Admin — System Info & API Management](screenshots/admin-panel-system.png)

**API Keys & Credentials** management with visual indicators. **Feature flags** toggles for runtime configuration. A full **configuration editor** with inline editing for every `config.yaml` parameter. **API usage & cost tracking** with per-provider breakdowns. **Database management** with table row counts, export capabilities, backup rotation, and a danger zone for maintenance operations. **Live log viewer** showing the tail of `bot.log`.

---

### Documentation — Built-in Reference Guide

![Documentation — 28-Section Reference Guide](screenshots/documentation-tab.png)

A complete **28-section reference guide** is embedded directly in the dashboard — covering architecture, the full trading pipeline, market discovery, research engine, forecasting ensemble, calibration, edge calculation, risk management, position sizing, drawdown system, order execution, whale scanner, decision intelligence, strategies, API connectors, storage, observability, alerts, configuration reference, CLI commands, safety, deployment, and a glossary. Searchable sidebar navigation with code blocks, tables, and callout boxes.

---

## ⚡ Getting Started

### Prerequisites

- Python 3.9+
- At minimum: `OPENAI_API_KEY` and one search API key (`TAVILY_API_KEY`, `SERPAPI_KEY`, or `BING_API_KEY`)

### Installation

```bash
git clone https://github.com/dylanpersonguy/Fully-Autonomous-Polymarket-AI-Trading-Bot.git
cd Fully-Autonomous-Polymarket-AI-Trading-Bot
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
```

### Configuration

```bash
cp .env.example .env
```

Add your API keys to `.env`:

| Variable | Required | Purpose |
|----------|----------|---------|
| `OPENAI_API_KEY` | **Yes** | GPT-4o for primary forecasting |
| `TAVILY_API_KEY` | **Yes**\* | Web search for evidence gathering |
| `SERPAPI_KEY` | Alt\* | Alternative search provider |
| `BING_API_KEY` | Alt\* | Alternative search provider |
| `ANTHROPIC_API_KEY` | No | Claude 3.5 Sonnet for ensemble |
| `GOOGLE_API_KEY` | No | Gemini 1.5 Pro for ensemble |
| `DASHBOARD_API_KEY` | No | Protect the dashboard with auth |
| `SENTRY_DSN` | No | Error tracking via Sentry |

\* At least one search provider is required. The system supports automatic fallback across all three.

### Launch

```bash
make dashboard
```

Open **http://localhost:2345** — the trading engine auto-starts in the background in paper mode.

---

## 🏗️ Architecture

```
src/
├── analytics/          # Adaptive weights, calibration feedback, regime detection, smart entry
├── connectors/         # Polymarket CLOB, Gamma API, web search, WebSocket feed, rate limiter
├── dashboard/          # Flask app, templates, static assets (CSS/JS)
├── engine/             # Trading loop, market classifier, market filter, position manager
├── execution/          # Order builder, order router, fill tracker, cancel handler
├── forecast/           # LLM forecaster, multi-model ensemble, feature builder, calibrator
├── observability/      # Structured logging, metrics, alerts (Telegram/Discord/Slack), Sentry
├── policy/             # Risk limits, edge calc, position sizer, drawdown, portfolio risk, arbitrage
├── research/           # Evidence extractor, query builder, source fetcher
└── storage/            # SQLite with WAL, migrations, cache, audit trail, backup
```

### Trading Pipeline

```
Market Discovery → Pre-Research Filter → Evidence Gathering → Multi-Model Forecasting
    → Calibration → Edge Calculation → 15-Point Risk Check → Position Sizing → Execution
```

Each cycle, the engine:

1. **Scans** active markets from Polymarket Gamma API with volume, liquidity, and spread filters
2. **Classifies** markets into 11 categories using 100+ regex rules (zero LLM cost)
3. **Filters** with a pre-research quality score — blocks junk markets before any API calls (~90% cost savings)
4. **Researches** via site-restricted searches per category (`site:bls.gov` for macro, `site:sec.gov` for corporate) with contrarian queries to avoid confirmation bias
5. **Forecasts** with a 3-model ensemble (GPT-4o 40%, Claude 3.5 Sonnet 35%, Gemini 1.5 Pro 25%) running in parallel
6. **Calibrates** using Platt scaling, historical calibration, evidence quality penalty, and ensemble spread penalty
7. **Validates** through 15+ independent risk checks — any failure blocks the trade
8. **Sizes** positions using fractional Kelly with 7 multipliers (confidence, drawdown, timeline, volatility, regime, category, liquidity)
9. **Executes** via auto-selected strategy (Simple, TWAP, Iceberg, or Adaptive based on order size and book depth)
10. **Monitors** with dynamic stop-loss, trailing stops, time-based exits, and edge reversal detection

---

## 🔬 Core Features

### Multi-Model AI Forecasting

Three frontier LLMs run in parallel, each producing an independent probability forecast:

| Model | Default Weight | Role |
|-------|---------------|------|
| GPT-4o | 40% | Primary forecaster |
| Claude 3.5 Sonnet | 35% | Second opinion |
| Gemini 1.5 Pro | 25% | Third opinion |

- **3 aggregation methods** — trimmed mean, median, or weighted average
- **Models forecast independently** — explicitly told not to anchor to market price
- **Graceful degradation** — if a model fails, the ensemble continues with remaining models
- **Adaptive weighting** — tracks per-model Brier scores by category and reweights over time

### Autonomous Research Engine

- **Query builder** generates site-restricted searches per category — `site:bls.gov` for macro, `site:sec.gov` for corporate, `site:fec.gov` for elections
- **Contrarian queries** to actively seek disconfirming evidence
- **3 pluggable search backends** — SerpAPI, Bing, Tavily — with automatic fallback
- **Full HTML extraction** via BeautifulSoup, not just search snippets
- **Domain authority scoring** — primary sources (1.0) > secondary (0.6) > unknown (0.3)
- **Auto-filters** low-quality domains (Wikipedia, Reddit, Medium, Twitter, TikTok)

### Calibration & Self-Improvement

- **Platt scaling** — logistic compression pulling extreme probabilities toward 0.50
- **Historical calibration** — logistic regression on past forecast vs. outcome pairs
- **Evidence quality penalty** — weak evidence shifts the forecast toward 0.50
- **Contradiction penalty** — conflicting sources increase uncertainty
- **Ensemble spread penalty** — model disagreement > 10% adds uncertainty
- **Auto-retraining** — recalibrates automatically after 30+ resolved markets
- **Brier score tracking** — continuous forecast accuracy monitoring

### Risk Management — 15+ Independent Checks

Every trade must pass **all** checks — a single failure blocks execution:

| # | Check | Default |
|---|-------|---------|
| 1 | Kill switch — manual emergency halt | Off |
| 2 | Drawdown auto-kill | 20% max |
| 3 | 4-level heat system (Normal → Warning → Critical → Max) | Progressive sizing cuts |
| 4 | Max stake per market | $50 |
| 5 | Daily loss limit | $500 |
| 6 | Max open positions | 25 |
| 7 | Minimum net edge after fees | 4% |
| 8 | Minimum liquidity | $2,000 |
| 9 | Maximum spread | 6% |
| 10 | Evidence quality threshold | 0.55 |
| 11 | Confidence filter | MEDIUM minimum |
| 12 | Implied probability floor | 5% |
| 13 | Category exposure cap | 35% per category |
| 14 | Timeline / endgame check | 48h to resolution |
| 15 | Arbitrage detection | Mispriced complementary markets |

### Drawdown Heat System

| Level | Threshold | Effect |
|-------|-----------|--------|
| 🟢 **Normal** | < 10% | Full position sizing |
| 🟡 **Warning** | ≥ 10% | Half sizing |
| 🟠 **Critical** | ≥ 15% | Quarter sizing |
| 🔴 **Max** | ≥ 20% | All trading halted |

### Smart Order Execution

- **Auto strategy selection** based on order size and book depth:
  - **Simple** — single limit order for small trades
  - **TWAP** — 5 time-weighted slices for large orders
  - **Iceberg** — shows only 20% of true order size
  - **Adaptive** — adjusts pricing based on real-time orderbook depth
- **Fill tracker** monitors fill rate, slippage, and time-to-fill per strategy
- **6 exit strategies** — dynamic stop-loss, trailing stop, hold-to-resolution, time-based, edge reversal, kill switch forced exit

### Triple Dry-Run Safety Gate

Three independent flags must **all** allow live trading — any one being off keeps you in paper mode:

```
Order.dry_run = False             ← per-order flag
config.execution.dry_run = False  ← config.yaml
ENABLE_LIVE_TRADING = true        ← environment variable
```

### Whale & Smart Money Intelligence

- **Auto-discovers** top 50 wallets by profit and top 50 by volume from the Polymarket leaderboard
- **Delta detection** — spots new entries, exits, size increases, and decreases
- **Conviction scoring** — whale count × dollar size = actionable signal
- **Edge integration** — whales agree with model → +8% edge boost; disagree → -2% penalty
- **7-phase liquid scanner pipeline** — seeds wallets → fetches markets → scans trades → per-market scan → ranks → deep analysis → scores & saves
- **API pool** rotates requests with round-robin, least-loaded, or weighted-random strategies

### Market Microstructure

- **Order flow imbalance** across 60min, 4hr, and 24hr windows
- **VWAP divergence** — signals entry when price is below volume-weighted average
- **Whale order detection** — flags individual trades above $2,000
- **Trade acceleration** — detects unusual activity surges (>2× baseline)
- **Book depth ratio** — measures bid vs. ask pressure
- **Smart entry calculator** — combines all signals for optimal entry price

### Observability & Alerting

- **structlog** JSON logging with automatic sensitive data redaction
- **Multi-channel alerts** — Telegram, Discord, Slack (with cooldowns)
- **Alert triggers** — trades, drawdown warnings, kill switch, errors, daily summaries
- **Sentry integration** — optional error tracking with data scrubbing
- **API cost tracking** — per-call cost estimation for LLM and search usage

### Storage & Audit

- **SQLite with WAL mode** for concurrent reads and writes
- **10 automatic schema migrations** — zero-downtime upgrades
- **Immutable audit trail** — every decision recorded with SHA-256 integrity checksums
- **TTL cache** — search results (1hr), orderbook (30s), LLM responses (30min), market list (5min)
- **Automated backups** with rotation (max 10)

---

## 🖥️ CLI Reference

```bash
# Market Discovery
bot scan --limit 20                  # Discover and list candidate markets

# Research & Forecasting
bot research --market <ID>           # Deep-dive research on a specific market
bot forecast --market <ID>           # Full pipeline: research → forecast → risk → size

# Trading
bot paper-trade --market <ID>        # Simulated trade execution
bot trade --market <ID>              # Live trade (requires ENABLE_LIVE_TRADING=true)

# Engine
bot engine start                     # Start continuous trading loop
bot engine status                    # Engine health check

# Dashboard
bot dashboard                        # Launch web UI on port 2345
bot dashboard --port 3333            # Custom port
bot dashboard --no-engine            # Dashboard only, no auto-start engine

# Portfolio & Risk
bot portfolio                        # Portfolio risk report
bot drawdown                         # Drawdown status and heat level
bot arbitrage                        # Scan for arbitrage opportunities
bot alerts                           # Alert history
```

---

## ⚙️ Configuration

All configuration lives in `config.yaml` and `.env`. Key sections:

<details>
<summary><strong>Scanning & Market Discovery</strong></summary>

```yaml
scanning:
  min_volume_usd: 1000
  min_liquidity_usd: 500
  max_spread: 0.08
  max_days_to_expiry: 120
  batch_size: 100
  preferred_types: [MACRO, ELECTION, CORPORATE, LEGAL, TECHNOLOGY, SCIENCE]
  restricted_types: [WEATHER]
  filter_min_score: 25
  research_cooldown_minutes: 60
```

</details>

<details>
<summary><strong>Forecasting & Ensemble</strong></summary>

```yaml
forecasting:
  llm_model: gpt-4o
  llm_temperature: 0.2
  llm_max_tokens: 4096
  min_evidence_quality: 0.55
  min_confidence_level: MEDIUM

ensemble:
  enabled: true
  models: [gpt-4o, claude-3-5-sonnet-20241022, gemini-1.5-pro]
  aggregation: trimmed_mean
  min_models_required: 1
  timeout_per_model_secs: 30
```

</details>

<details>
<summary><strong>Risk Management</strong></summary>

```yaml
risk:
  max_stake_per_market: 50.0
  max_daily_loss: 500.0
  max_open_positions: 25
  min_edge: 0.04
  min_liquidity: 2000
  max_spread: 0.06
  kelly_fraction: 0.25
  bankroll: 5000.0
  stop_loss_pct: 0.2
  take_profit_pct: 0.3

drawdown:
  enabled: true
  max_drawdown_pct: 0.2
  warning_drawdown_pct: 0.1
  critical_drawdown_pct: 0.15
  auto_kill_at_max: true

portfolio:
  max_category_exposure_pct: 0.35
  max_single_event_exposure_pct: 0.25
  max_correlated_positions: 4
```

</details>

<details>
<summary><strong>Execution & Engine</strong></summary>

```yaml
execution:
  dry_run: true
  default_order_type: limit
  slippage_tolerance: 0.01

engine:
  scan_interval_minutes: 10
  max_markets_per_cycle: 10
  paper_mode: true
  cycle_interval_secs: 180
```

</details>

<details>
<summary><strong>Whale Scanner</strong></summary>

```yaml
wallet_scanner:
  enabled: true
  scan_interval_minutes: 15
  min_whale_count: 1
  min_conviction_score: 15.0
  max_wallets: 20
  conviction_edge_boost: 0.08
  conviction_edge_penalty: 0.02
```

</details>

---

## 🚀 Deployment

### Local Development

```bash
make dashboard       # Flask dev server on port 2345
```

### Production (Gunicorn)

```bash
make gunicorn        # Production WSGI server
```

### Docker

```bash
cp .env.example .env
# Edit .env with your API keys
docker compose up -d
```

The Docker setup includes:
- **Two-stage build** for minimal image size
- **Non-root user** (`botuser`) for security
- **Persistent volumes** for database, logs, and reports
- **Health checks** with 30s intervals
- **Resource limits** (1 GB memory, 1.0 CPU)
- **Auto-restart** policy (`unless-stopped`)

### Health Endpoints

| Endpoint | Purpose | Auth |
|----------|---------|------|
| `GET /health` | Liveness probe | Open |
| `GET /ready` | Readiness check (DB + engine) | Open |
| `GET /metrics` | Prometheus-compatible metrics | Open |

---

## 🧪 Testing

```bash
make test            # Run all tests
make test-cov        # Tests with coverage report
make lint            # Ruff linter
make format          # Auto-format code
make typecheck       # mypy type checking
```

---

## 🔐 Safety & Security

- **Dry run by default** — three independent gates must all allow live trading
- **4-level drawdown heat system** — progressively cuts position sizes, halts at 20%
- **No secrets in codebase** — everything via `.env` and environment variables
- **Docker runs as non-root** — restricted container permissions
- **API key redaction** — structlog automatically scrubs sensitive data from logs
- **SHA-256 audit integrity** — tamper-evident decision records
- **Dashboard authentication** — optional `DASHBOARD_API_KEY` protection
- **Rate limiting** — configurable API pool prevents endpoint abuse

---

## 🛠️ Makefile Commands

| Command | Description |
|---------|-------------|
| `make install` | Install production dependencies |
| `make dev` | Install with dev + prod dependencies |
| `make test` | Run all tests |
| `make test-cov` | Tests with coverage report |
| `make lint` | Run ruff linter |
| `make format` | Auto-format code |
| `make typecheck` | mypy type checking |
| `make dashboard` | Start dashboard on port 2345 |
| `make engine` | Start headless trading engine |
| `make scan` | Run single market scan |
| `make gunicorn` | Production WSGI server |
| `make docker` | Build Docker image |
| `make docker-up` | Start docker compose |
| `make docker-down` | Stop docker compose |
| `make backup` | Backup SQLite database |
| `make clean` | Remove build artifacts |

---

## 📬 Custom Bot Development

**Want a custom trading bot tailored to your strategy?**

I build custom automated trading bots for prediction markets, crypto, and forex. Whether you need modifications to this platform or an entirely new system, I can help.

**📱 Contact: [@DylanForexia](https://t.me/DylanForexia) on Telegram**

Services include:

- **Custom strategy development & backtesting** — Build and validate strategies against historical data
- **Live trading integration with exchange APIs** — Polymarket, Binance, dYdX, forex brokers, and more
- **Risk management system design** — Position sizing, drawdown protection, portfolio risk controls
- **Dashboard & monitoring tools** — Real-time web dashboards with alerting and audit trails
- **Performance optimization & scaling** — Low-latency execution, concurrent processing, cloud deployment

---

## ❓ FAQ

<details>
<summary><strong>What is this Polymarket bot?</strong></summary>

This is an open-source automated trading bot for [Polymarket](https://polymarket.com), the largest prediction market platform. It uses AI (GPT-4o, Claude, Gemini) to research events, forecast probabilities, and execute trades autonomously with strict risk management.

</details>

<details>
<summary><strong>Is this Polymarket bot free?</strong></summary>

Yes, the bot is fully open source under the MIT license. You will need API keys for OpenAI and a search provider (Tavily, SerpAPI, or Bing) which have their own costs.

</details>

<details>
<summary><strong>Can I use this bot for live trading on Polymarket?</strong></summary>

Yes. The bot supports both paper trading (simulated) and live trading. Paper mode is enabled by default — you must explicitly unlock three independent safety gates to enable real order execution on Polymarket's CLOB.

</details>

<details>
<summary><strong>What AI models does the Polymarket bot use?</strong></summary>

The bot runs a multi-model ensemble with GPT-4o (40% weight), Claude 3.5 Sonnet (35%), and Gemini 1.5 Pro (25%). Models forecast independently and the results are aggregated using trimmed mean, median, or weighted average.

</details>

<details>
<summary><strong>How does the whale tracker work?</strong></summary>

The bot auto-discovers the top 100 Polymarket wallets by profit and volume, monitors their positions in real time, and generates conviction signals when multiple whales converge on the same market. These signals boost or penalize edge calculations.

</details>

<details>
<summary><strong>Does this work with the Polymarket API?</strong></summary>

Yes. The bot integrates with both the Polymarket Gamma API (for market discovery) and the Polymarket CLOB API (for order execution). It also supports WebSocket feeds for real-time price data.

</details>

---

## 🌐 Related Topics

This Polymarket trading bot is relevant for anyone interested in:

- **Prediction market trading** — Automated strategies for event-based markets
- **Polymarket API integration** — Building on Polymarket's CLOB and Gamma APIs
- **AI-powered trading** — Using large language models (LLMs) for market forecasting
- **Algorithmic trading bots** — Autonomous systems with risk management and position sizing
- **Whale tracking & smart money** — Following top traders on prediction markets
- **Kelly criterion position sizing** — Mathematically optimal bet sizing with multiple adjustment factors
- **Quantitative trading** — Systematic approaches to prediction market alpha

---

## 📄 License

MIT

---

<div align="center">

**Built for the prediction market community.**

**⭐ Star this repo** if you find it useful — it helps others discover this Polymarket trading bot.

*This software is for educational and research purposes. Not financial advice. Trade responsibly.*

</div>
