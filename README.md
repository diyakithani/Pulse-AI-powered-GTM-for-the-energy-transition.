# 🌿 Pulse — Climate GTM Intelligence

**Built by Diya Kithani as a vibe-coded application for the AZX GTM AI Stack role.**

Pulse is a climate-native GTM intelligence platform — the kind of tool AZX would actually use to find, understand, and convert prospects in energy, utilities, and real estate. It's not a portfolio piece pretending to be a product. It's a working prototype of what I'd build on day one.

---

## What it does

| Screen | What it shows |
|---|---|
| **Dashboard** | Pipeline overview, CO₂e impact counter, live climate signal feed, top accounts to action |
| **Prospect Intelligence** | AI-scored accounts with ICP score, mission alignment score, mandate clock, and CO₂e impact estimate |
| **Outreach AI** | Claude-powered email generator — 5 tones including mission-first, streams live, personalized to each prospect's climate context |
| **Climate Signal Feed** | Mandate deadlines, IRA/DOE funding alerts, emissions misses, policy changes, news hooks |
| **Sustainability Report Analyzer** | Paste any ESG report → Claude extracts gaps, outreach hooks, mandate exposure, and the AZX angle |
| **Funnel** | Conversion rates with mission score distribution — mission-aligned accounts close at 68% vs 41% |
| **Campaigns** | Performance tracker showing AI + climate-angle emails outperform standard outreach by 62% |

---

## How the AI works

Pulse calls the **Anthropic Claude API** (`claude-sonnet-4-20250514`) directly from the browser for two features:

1. **Outreach email generator** — streams a personalized cold email based on the prospect's ICP score, mission score, mandate deadline, triggering signal, and selected tone
2. **Sustainability report analyzer** — sends the pasted ESG report text to Claude and gets back a structured analysis: commitments made, gaps vs targets, outreach hooks, and the AZX angle

---

## Running the app

### Option A: Claude.ai (zero setup)
Open `index.html` as an artifact in Claude.ai. The API key is injected automatically — AI features work instantly, no configuration needed.

### Option B: Netlify Drop (30 seconds, free)
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag `index.html` onto the page
3. Get a live URL instantly
4. When the app loads, you'll see a yellow banner — enter your Anthropic API key there
5. The key is stored in `sessionStorage` (browser memory only, never sent anywhere except Anthropic)

### Option C: GitHub Pages
```bash
# Create a new repo, add index.html, enable Pages in settings
git init
git add index.html README.md
git commit -m "Pulse v2 — climate GTM intelligence"
git remote add origin https://github.com/YOUR_USERNAME/pulse-gtm.git
git push -u origin main
# Then: Settings → Pages → Deploy from branch → main
```

### Option D: Local
```bash
# Just open it — no build step, no dependencies
open index.html
# or
python3 -m http.server 8080
# then visit http://localhost:8080
```

---

## Getting an Anthropic API key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign up / log in
3. Navigate to **API Keys** → **Create Key**
4. Copy the key (starts with `sk-ant-api03-...`)
5. Paste it into the yellow banner in Pulse when running externally

> **Security note:** The key is stored in `sessionStorage` — it lives only in your browser tab and is cleared when you close the tab. It's never logged, stored on a server, or sent anywhere except directly to `api.anthropic.com`. For a production deployment, move the API calls to a backend proxy so the key never touches the client.

---

## API cost estimate

Each email generation: ~$0.003–0.005 (500 tokens out)  
Each report analysis: ~$0.005–0.010 (800 tokens out)  

Very cheap to demo. A full day of heavy use would cost < $1.

---

## Tech stack

| Layer | Choice | Why |
|---|---|---|
| UI | Vanilla HTML/CSS/JS | Zero build step, instant deploy, fully portable |
| Fonts | Instrument Serif + Geist + Geist Mono | Distinctive — not Inter |
| AI | Anthropic Claude Sonnet 4 | Best-in-class for structured, nuanced text generation |
| Hosting | Any static host | No server needed |
| State | In-memory JS | No database, no backend |

No frameworks. No npm. No build step. Just one file.

---

## What I'd build next (production version)

- **Backend proxy** for the API key (never expose in client)
- **HubSpot integration** — write generated emails + prospect profiles directly to CRM
- **Real signal ingestion** — connect to news APIs, SEC filings, job posting feeds, regulatory databases
- **Slack notifications** — push high-priority signals to `#gtm-signals` automatically
- **Collateral search** — embed AZX's GitHub markdown repo and surface relevant case studies per prospect
- **n8n workflows** — automate the full signal → score → draft → CRM pipeline

---

## About the builder

**Diya Kithani** — AI Product Manager & Data Engineer  
This app is my application for the GTM AI Stack role at AZX.  
It's also a live demo of what I'd build for the team.

---

*Built with Claude. Deployed with intention.*
