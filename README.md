# FSL Trading Desk — Multi-Agent v2

A multi-agent crypto trading analysis desk powered by **Bitget AgentHub Skills** + **Claude**.

Four AI agents debate a trade in real time — Market Analyst, News Agent, Risk Manager, and Execution Agent — using live Bitget market data before reaching a final verdict.

---

## Project Structure

```
fsl-trading-desk/
├── api/
│   └── analyze.js        ← Vercel serverless proxy (keeps API key server-side)
├── public/
│   └── index.html        ← Full frontend (HTML/CSS/JS, no build step)
├── vercel.json           ← Vercel routing config
├── package.json
└── README.md
```

---

## Deploy to Vercel (5 minutes)

### Step 1 — Push to GitHub

```bash
git init
git add .
git commit -m "FSL Trading Desk v2"
git remote add origin https://github.com/YOUR_USERNAME/fsl-trading-desk.git
git push -u origin main
```

### Step 2 — Connect to Vercel

1. Go to [vercel.com](https://vercel.com) → New Project
2. Import your GitHub repo
3. Leave all build settings as default — Vercel auto-detects the config

### Step 3 — Add your Anthropic API key

In the Vercel dashboard:
- Go to **Project Settings → Environment Variables**
- Add: `ANTHROPIC_API_KEY` = your key from [console.anthropic.com](https://console.anthropic.com)
- Click **Save**, then **Redeploy**

That's it. Your app is live.

---

## APIs Used

| API | Purpose | Auth Required |
|-----|---------|--------------|
| `api.bitget.com/api/v2/spot/market/tickers` | Live price, 24h change, volume | None (public) |
| `api.bitget.com/api/v2/mix/market/current-fund-rate` | Futures funding rate | None (public) |
| `api.anthropic.com/v1/messages` | Claude agent engine | API key (server-side via proxy) |

---

## Local Development

```bash
npm install -g vercel
vercel dev
```

Then open `http://localhost:3000`

The `/api/analyze` proxy function runs locally via Vercel CLI. Add a `.env.local` file:

```
ANTHROPIC_API_KEY=sk-ant-...
```

---

## Bitget AgentHub Skills Used

- Market Data Skill
- Sentiment Skill  
- Technical Signal Skill
- Execution Skill

---

*Not financial advice. Built for the Bitget Agent Hub Skills Challenge.*
