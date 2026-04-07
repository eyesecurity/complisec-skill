<p align="center">
  <img src="https://img.shields.io/badge/complisec-v2.0.0-blue?style=flat-square" alt="version" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="license" />
  <img src="https://img.shields.io/badge/NIS2-ready-green?style=flat-square" alt="NIS2" />
  <img src="https://img.shields.io/badge/GDPR-ready-green?style=flat-square" alt="GDPR" />
</p>

<h1 align="center">complisec</h1>

<p align="center">
  <strong>EU compliance enforcement for AI agents.</strong><br>
  <a href="https://skills.eye.security/eu-compliance/">skills.eye.security/eu-compliance</a>
</p>

---

## What is complisec?

One skill that onboards your organisation, builds a compliance profile, and enforces EU compliance when it matters — code generation, cloud integrations, deployments, data handling, and regulatory discussions.

## What to expect

You don't need to know complisec exists — it activates when your prompt carries compliance risk.

| You say | complisec does |
|---------|---------------|
| "Write an API endpoint that stores customer records" | Flags personal data handling, enforces audit logging, checks data residency against your profile |
| "Add Stripe integration to the checkout flow" | Detects new supplier not in your profile, asks about DPA status and data hosting region |
| "Our monitoring detected unauthorized access last night" | Starts incident lifecycle, calculates NIS2 24h/72h notification deadlines, identifies affected critical assets |
| "Deploy the new database migration to production" | Triggers change management for critical asset, requires impact assessment and rollback plan |
| "Here's the config: DB_PASSWORD=hunter2" | Blocks immediately, never echoes the secret, warns to rotate credentials |
| "Are we compliant with NIS2?" | Runs applicability check, offers 39-control gap analysis with 5-level maturity scoring |
| "We're switching from AWS to Azure for hosting" | Checks data residency constraints, flags affected critical assets, validates new supplier |

## Install

### Claude Code

Add the Eye Security marketplace and install complisec:

```
/plugin marketplace add eyesecurity/skills
/plugin install complisec
```

Or clone locally:

```bash
git clone https://github.com/eyesecurity/skills.git
# Then in Claude Code:
/plugin marketplace add ./skills
/plugin install complisec
```

### OpenAI Codex

Clone the repo into your project — Codex reads `AGENTS.md` automatically from the project root:

```bash
git clone https://github.com/eyesecurity/skills.git
```

### Other coding agents (Cursor, Copilot, Windsurf, Cline)

Clone the repo into your project, then point your agent at the skill:

```bash
git clone https://github.com/eyesecurity/skills.git
```

Say: **"Read `skills/plugins/complisec/SKILL.md` and follow its instructions."**

### Any AI chat (ChatGPT, Claude.ai, Mistral, Grok)

1. Download [complisec.zip](https://github.com/eyesecurity/skills/releases/latest/download/complisec.zip)
2. Upload the ZIP to your AI chat
3. Say: **"Read SKILL.md and follow its instructions."**

### Profile example

See [`plugins/complisec/.compliance/profile.example.json`](plugins/complisec/.compliance/profile.example.json) for what an org profile looks like — a compact ~25-line JSON block capturing your critical assets, data residency, risk appetite, suppliers, and legal obligations.

### Python requirement

Only the `nis2-gap-analysis` sub-skill needs Python 3.10+ (for the NIS2 applicability checker). Everything else is pure markdown — no dependencies.

## Skills

| Skill | What it does |
|-------|-------------|
| **complisec** (root) | Onboarding questionnaire + profile-aware enforcement on compliance-relevant actions |
| **nis2-gap-analysis** | 5-level maturity NIS2/Cbw assessment with consultant field methodology |
| **incident-management** | Structured incident lifecycle with NIS2 24/72h/30d + GDPR 72h deadline tracking and EU reporting directory |
| **vendor-risk** | Vendor assessment, DPA tracking, data residency checks, NIS2 Art. 21(2)(d) supply chain |
| **change-management** | Change records for critical assets with impact classification, approval workflow, rollback plans |
| **audit-logging** | Structured audit logging for agent actions + enforce logging in AI-generated code |
| **data-sensitivity** | Data classification, prompt secret interception, scanning, blocking — patterns mapped to GDPR/NIS2 |
| **compliance-hub** | Central collection for all compliance records — cloud storage, immutability, observability |
| **security-compliance-tools** | Critical asset methodology, CISO workflow, EU compliance tooling index |
| **eu-compliance-directives** | Curated index of authoritative EU and national compliance sources — look up, don't hardcode |

## Need more?

Get expert guidance alongside the tool. [Eye Security](https://www.eye.security/en/contact/eu-regulations?utm_source=skills_eye_security&utm_medium=cta&utm_campaign=377720011-2026_Q2_proj-ai-compliance-skill&utm_content=eu_regulations_contact) helps EU organisations implement compliance end-to-end — from NIS2 readiness to managed detection and response.

[Talk to our team →](https://www.eye.security/en/contact/eu-regulations?utm_source=skills_eye_security&utm_medium=cta&utm_campaign=377720011-2026_Q2_proj-ai-compliance-skill&utm_content=eu_regulations_contact)

## Project structure

```
skills/                                       # eyesecurity/skills repo
├── AGENTS.md                             # OpenAI Codex entrypoint
├── .claude-plugin/
│   └── marketplace.json                  # Eye Security plugin marketplace
├── plugins/
│   └── complisec/                        # complisec plugin
│       ├── SKILL.md                      # Root skill — onboarding + enforcement
│       ├── .claude-plugin/
│       │   └── plugin.json               # Claude Code plugin manifest
│       ├── skills/
│       │   ├── complisec/                # Entry skill (for plugin convention)
│       │   ├── nis2-gap-analysis/        # NIS2 gap analysis + nis2_check.py
│       │   ├── incident-management/      # Incident lifecycle + EU reporting directory
│       │   ├── vendor-risk/              # Supply chain risk management
│       │   ├── change-management/        # Change records for critical assets
│       │   ├── audit-logging/            # Audit logging + schemas
│       │   ├── data-sensitivity/         # Classification + scanning + blocking
│       │   ├── compliance-hub/           # Central log collection + observability
│       │   ├── org-profile/              # Organisation profile builder
│       │   ├── security-compliance-tools/# Critical asset methodology + compliance tools
│       │   └── eu-compliance-directives/ # EU + national source index
│       └── .compliance/
│           └── profile.example.json      # Example org profile
└── README.md
```

## License

MIT
