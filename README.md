#  Multi-Agent Autonomous Trading Floor using MCP, Ollama, Serper Search, and Polygon APIs

> An end-to-end Multi-Agent Autonomous Trading Platform that combines Model Context Protocol (MCP), Local LLMs, Real-Time Market Intelligence, Portfolio Management, and Autonomous Decision-Making to simulate a professional AI-powered trading floor.

---

##  Overview

This project implements a Multi-Agent Autonomous Trading Floor where multiple AI traders independently analyze market conditions, perform research, manage portfolios, execute trades, and rebalance investments using MCP-enabled tools and resources.

The system combines:

- Model Context Protocol (MCP)
- Ollama (Qwen 2.5)
- Polygon Market Data API
- Serper Search API
- FastMCP Servers
- Multi-Agent Architecture
- Portfolio Management
- Autonomous Trading Workflows
- Agent Tracing and Observability

Unlike traditional trading bots that rely on fixed rules, each trader operates with a unique investment philosophy and can independently make trading decisions based on market research, live stock prices, account status, and portfolio strategies.

---

#  System Architecture

```text
┌──────────────────────────────────────────────┐
│               Trading Floor                  │
└──────────────────────────────────────────────┘
                      │
                      ▼

      ┌─────────────┬─────────────┬─────────────┬─────────────┐
      │             │             │             │
      ▼             ▼             ▼             ▼

  Warren         George         Ray          Cathie
(Value)         (Macro)     (Risk Parity)  (Innovation)

      │             │             │             │
      └─────────────┴─────────────┴─────────────┘
                            │
                            ▼

                  Research Agent (Qwen 2.5)

                            │

              ┌─────────────┴─────────────┐
              │                           │

              ▼                           ▼

       Serper Search API          Polygon Market API

              │                           │
              └─────────────┬─────────────┘
                            │
                            ▼

                  MCP Tool & Resource Layer

                            │

     ┌─────────────────────────────────────────┐
     │ Accounts MCP Server                     │
     │ Market MCP Server                       │
     │ Push Notification MCP Server            │
     └─────────────────────────────────────────┘

                            │
                            ▼

                    Portfolio Database
```

---

#  Key Features

###  Multi-Agent Trading System

Four autonomous traders operate independently:

| Trader | Inspired By | Investment Style |
|----------|----------|----------|
| Warren | Warren Buffett | Value Investing |
| George | George Soros | Macro Trading |
| Ray | Ray Dalio | Diversified Risk Parity |
| Cathie | Cathie Wood | Innovation & Crypto ETFs |

Each trader:

- Maintains a separate portfolio
- Has a unique investment strategy
- Performs independent research
- Makes autonomous buy/sell decisions
- Rebalances holdings over time

---

###  Autonomous Market Research

A dedicated Research Agent:

- Searches current financial news
- Analyzes market trends
- Evaluates bullish and bearish signals
- Identifies investment opportunities
- Produces structured market reports

Powered by:

- Serper Search API
- Qwen 2.5
- MCP Tool Calling

---

###  Real-Time Market Intelligence

The system retrieves:

- Live Stock Prices
- Market Data
- Company Information
- Financial Signals

Using:

- Polygon API

---

### ⚙ MCP Integration

The project demonstrates practical implementation of the Model Context Protocol through:

### MCP Tools

```python
get_balance()
get_holdings()
buy_shares()
sell_shares()
change_strategy()
```

### MCP Resources

```text
accounts://accounts_server/{name}

accounts://strategy/{name}
```

The AI agents use MCP to interact with external services and account data.

---

###  Portfolio Management

Each trader has:

- Cash Balance
- Holdings Tracking
- Trade History
- Portfolio Valuation
- Profit & Loss Monitoring
- Strategy Management

Implemented through:

```text
accounts.py
accounts_server.py
database.py
```

---

###  Continuous Autonomous Trading

The trading floor can operate continuously:

```text
Research
   ↓
Analyze
   ↓
Trade
   ↓
Update Portfolio
   ↓
Rebalance
   ↓
Repeat
```

This simulates a real-world autonomous trading environment.

---

###  Agent Observability

Integrated tracing allows monitoring:

- Agent Decisions
- Tool Calls
- Trading Activity
- Research Processes
- Execution Flows

Implemented using:

```text
tracers.py
OpenAI Tracing
Custom Trace IDs
```

---

#  AI Models Supported

The platform supports multiple models through dynamic model selection.

| Provider | Models |
|-----------|---------|
| Ollama | Qwen 2.5 |
| OpenAI | GPT Models |
| DeepSeek | DeepSeek Models |
| Google | Gemini Models |
| xAI | Grok Models |
| OpenRouter | Any OpenRouter Model |

Implemented via:

```python
get_model()
```

inside:

```text
traders.py
```

---

# 📂 Project Structure

```text
multi-agent-autonomous-trading-floor/

│
├── README.md
├── requirements.txt
├── .env.example
│
├── app.py
├── trading_floor.py
├── traders.py
│
├── accounts.py
├── accounts_server.py
├── accounts_client.py
│
├── market.py
├── market_server.py
│
├── database.py
├── util.py
│
├── mcp_params.py
├── templates.py
├── reset.py
├── tracers.py
├── push_server.py
│
├── autonomous.ipynb
├── 4_lab4.ipynb
│
└── screenshots/
```

---

# 🔧 Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/multi-agent-autonomous-trading-floor.git

cd multi-agent-autonomous-trading-floor
```

---

## Create Virtual Environment

```bash
python -m venv venv

source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

#  Environment Variables

Create a `.env` file:

```env
POLYGON_API_KEY=your_polygon_key

SERPER_API_KEY=your_serper_key

OPENAI_API_KEY=your_openai_key

DEEPSEEK_API_KEY=your_deepseek_key

GOOGLE_API_KEY=your_google_key

GROK_API_KEY=your_grok_key

OPENROUTER_API_KEY=your_openrouter_key
```

---

#  Running the Project

## Reset Traders

```bash
python reset.py
```

---

## Start Trading Floor

```bash
python trading_floor.py
```

---

## Launch Dashboard

```bash
python app.py
```

---

#  Example Workflow

### Step 1

Research Agent searches:

```text
Latest AI Stock Market News
```

---

### Step 2

Research summary generated:

```text
Bullish Signals
Bearish Signals
Top Stocks
Market Outlook
```

---

### Step 3

Trader evaluates:

- Strategy
- Holdings
- Cash Balance
- Market Report

---

### Step 4

Trader executes:

```python
buy_shares()

sell_shares()
```

through MCP Tools.

---

### Step 5

Portfolio updates automatically.

---

# ⚠ Challenges Faced & Solutions

## MCP Server Connection Issues

### Problem

```text
Connection Closed
```

### Solution

- Correct MCP server initialization
- Proper AsyncExitStack management

---

## Environment Variable Loading Issues

### Problem

```text
API Keys Not Loaded
```

### Solution

```python
load_dotenv(override=True)
```

---

## Python Executable Resolution

### Problem

```text
No such file or directory: python
```

### Solution

```python
python3
```

for macOS/Linux environments.

---

## MCP Schema Validation Errors

### Problem

```text
Expected float
Received string
```

### Solution

Updated MCP tool return types to match actual outputs.

---

#  Technologies Used

### AI & LLMs

- Ollama
- Qwen 2.5
- GPT
- Gemini
- DeepSeek
- Grok

### Agent Framework

- OpenAI Agents SDK
- MCP (Model Context Protocol)
- FastMCP

### Market Intelligence

- Polygon API
- Serper API

### Backend

- Python
- AsyncIO
- Pydantic

### Storage

- SQLite
- JSON Persistence

### Observability

- OpenAI Tracing
- Custom Trace Logging

---

#  Learning Outcomes

This project provided hands-on experience with:

- Agentic AI Systems
- MCP Architecture
- Tool Calling
- MCP Resources
- Multi-Agent Systems
- Portfolio Management
- Financial AI Applications
- Real-Time Market Data Integration
- Autonomous Decision-Making
- Async Python Programming
- AI Agent Observability
- Production-Style AI Workflows

---

#  Future Improvements

- Risk Management Engine
- Stop Loss Mechanisms
- Dynamic Position Sizing
- Portfolio Optimization
- Long-Term Agent Memory
- Reinforcement Learning Integration
- Multi-Asset Trading
- Crypto Trading Support
- Advanced Analytics Dashboard
- Distributed Agent Execution

---

# Author

**Prateek Choudhary**

M.Tech – IIIT Allahabad

Interests:

- Agentic AI
- Model Context Protocol (MCP)
- LLM Engineering
- Autonomous Systems
- Multi-Agent Architectures
- AI-Powered Financial Systems

---

## ⭐ If you found this project interesting, consider giving it a star.
