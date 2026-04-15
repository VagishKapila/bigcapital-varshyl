# BigCapital — Varshyl Self-Hosted

Self-hosted [Bigcapital](https://bigcapital.app) deployed on Railway for Varshyl Inc accounting.

## Services

| Service | Image | Purpose |
|---|---|---|
| **webapp** | `bigcapitalhq/webapp:latest` | React frontend (port 80) |
| **server** | `bigcapitalhq/server:latest` | Node.js API (port 3000) |
| **mysql** | Railway MySQL plugin | MariaDB database |
| **redis** | Railway Redis plugin | Queue + cache |
| **gotenberg** | `gotenberg/gotenberg:7` | PDF generation |

## Deploy on Railway

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template)

### Manual Setup

1. Go to [railway.app](https://railway.app) → New Project
2. Add MySQL plugin → note the connection vars
3. Add Redis plugin → note the connection vars
4. Add service from Docker image: `bigcapitalhq/server:latest`
5. Add service from Docker image: `bigcapitalhq/webapp:latest`
6. Add service from Docker image: `gotenberg/gotenberg:7`
7. Copy env vars from `.env` → set in Railway Dashboard
8. Generate domain for webapp service

## Environment Variables

See `.env` for the full list. Required before first deploy:
- `JWT_SECRET` — `openssl rand -base64 32`
- `BASE_URL` — your Railway domain (e.g., `https://bigcapital-varshyl-production.up.railway.app`)
- `MAIL_*` — SMTP credentials (use Resend with `noreply@varshyl.com`)

## Sessions

- **Session 2** — Railway deploy + service health check ← *current*
- **Session 3** — BigCapital initial config (org setup, chart of accounts)
- **Session 4** — Plaid bank sync integration
- **Session 5** — Varshyl products integration (Construction AI Billing → BigCapital)
