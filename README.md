#  LogPulse — AI-Powered Log Monitoring System

> A universal log monitoring system inspired by Kibana/ELK Stack, 
> with real-time AI alerting powered by n8n automation.

![Demo](https://img.shields.io/badge/status-live-brightgreen)
![n8n](https://img.shields.io/badge/automation-n8n-orange)
![AI](https://img.shields.io/badge/AI-Groq%20LLaMA-blue)

##  Live Demo
 [logpulse-monitor.github.io](https://aamerk01.github.io/logpulse-monitor/)

##  Architecture
```
Any App → Webhook → n8n Workflow → AI Analysis → Gmail Alert
                         ↓
              [No Alert] Calculate Stats
```

##  n8n Workflow (10 nodes)

| Node | Role |
|------|------|
| Webhook | Receives logs from any source |
| Code (JS) | Parses logs, counts errors, detects keywords |
| Should Alert? | IF node — checks error threshold |
| Enrich Alert Data | SET node — adds severity, timestamp |
| Route by Severity | SWITCH node — routes CRITICAL/HIGH/MEDIUM |
| OpenAI/Groq | AI analysis of log patterns |
| Format Email | Builds clean HTML email |
| Send Alert Email | Gmail notification |
| Calculate Stats | Computes error rate when no alert |
| Log to Console | Records non-alert executions |

##  Tech Stack

- **n8n Cloud** — workflow automation
- **Groq API (LLaMA 3.3)** — AI log analysis
- **Gmail OAuth2** — email alerts
- **GitHub Pages** — frontend hosting
- **Vanilla JS** — no framework needed

##  How to Use

### 1. Import the workflow
- Open n8n → Import → select `workflow.json`
- Configure credentials (Groq API + Gmail OAuth2)
- Publish the workflow

### 2. Configure LogPulse
- Open `index.html`
- Enter your webhook URL
- Click **Start** or **BATCH×5** to trigger an alert

### 3. Receive alerts
- Emails arrive with AI analysis within seconds
- Format: ISSUES / ROOT CAUSE / ACTION / SEVERITY

##  Screenshots

> Add screenshots here

##  What I Learned

- Building automation workflows with n8n
- Integrating LLM APIs for log analysis  
- CORS handling between frontend and webhooks
- Real-time monitoring dashboard design
- OAuth2 authentication with Gmail

##  License
MIT
