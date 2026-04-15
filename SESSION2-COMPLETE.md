# SESSION 2 COMPLETE — BigCapital Varshyl Railway Deploy
**Date:** April 15, 2026  
**Status:** ✅ ALL 5 SERVICES HEALTHY

---

## Deployed URLs

| Service | URL |
|---|---|
| **BigCapital App (webapp)** | https://webapp-production-1185.up.railway.app |
| **API Server** | https://server-production-874d4.up.railway.app |
| Railway Project | https://railway.app/project/91692aa0-fe68-4a78-b53e-90910156c5c8 |
| GitHub Repo | https://github.com/VagishKapila/bigcapital-varshyl |

---

## Service Health (verified 2026-04-15T09:51:20Z)

| Service | Image | Status |
|---|---|---|
| ✅ webapp | `bigcapitalhq/webapp:latest` | SUCCESS |
| ✅ server | `bigcapitalhq/server:latest` | SUCCESS |
| ✅ mysql | `mariadb:10.11` | SUCCESS |
| ✅ redis | `redis:7-alpine` | SUCCESS |
| ✅ gotenberg | `gotenberg/gotenberg:7` | SUCCESS |

---

## Railway Service IDs

```
Project ID:     91692aa0-fe68-4a78-b53e-90910156c5c8
Environment ID: 4ee6c70c-1be9-482e-9a23-b811e4850e3b

server:    2dbcf124-1975-4244-a48a-e23f1c82c099
webapp:    a22086fe-298b-4e17-abfd-e0ce5c96da2e
mysql:     987e54b3-eedf-47a7-86ce-629bc46bd267
redis:     bcb63cc8-2d30-46cc-8ae7-95f72c71a569
gotenberg: e53900c5-2760-4ee9-b141-686b38ce33e3
```

---

## Environment Variables Set on Server

| Variable | Value |
|---|---|
| `NODE_ENV` | production |
| `JWT_SECRET` | [set — 32 byte random] |
| `BASE_URL` | https://server-production-874d4.up.railway.app |
| `DB_HOST` | mysql.railway.internal |
| `DB_PORT` | 3306 |
| `DB_USER` | bigcapital |
| `DB_PASSWORD` | bigcapital_pass |
| `DB_CHARSET` | utf8 |
| `SYSTEM_DB_NAME` | bigcapital_system |
| `TENANT_DB_NAME_PERFIX` | bigcapital_tenant_ |
| `REDIS_HOST` | redis.railway.internal |
| `REDIS_PORT` | 6379 |
| `MAIL_HOST` | smtp.resend.com |
| `MAIL_PORT` | 587 |
| `MAIL_FROM_ADDRESS` | noreply@varshyl.com |
| `GOTENBERG_URL` | http://gotenberg.railway.internal:3000 |
| `S3_REGION` | us-east-1 |
| `S3_BUCKET` | dpstudio-documents (shared, using bigcapital/ prefix) |
| `S3_ACCESS_KEY_ID` | [set — dpstudio IAM key] |
| `S3_SECRET_ACCESS_KEY` | [set — masked] |
| `SIGNUP_DISABLED` | false |
| `BANK_FEED_ENABLED` | false |
| `PLAID_ENV` | sandbox |

---

## Pending Before Using BigCapital

1. **MAIL_PASSWORD** — Add your Resend API key to Railway server vars
   - Go to: Railway → bigcapital-varshyl → server → Variables
   - Add: `MAIL_PASSWORD` = your Resend API key (starts with `re_`)

2. **First login** — Navigate to https://webapp-production-1185.up.railway.app
   - Create the first admin account (signup is enabled)

3. **S3 bucket isolation** — Consider creating a dedicated `bigcapital-varshyl-docs` S3 bucket
   - Currently sharing `dpstudio-documents` bucket with DocuFlow
   - Low risk (different key prefixes) but cleaner to separate

---

## What Was Built

- **GitHub:** `VagishKapila/bigcapital-varshyl` with Railway config, compose files, env template
- **Railway project:** 5 services deployed from Docker Hub images
- **Crash fix:** `Error: bucket is required` — fixed by setting S3 vars from DocuFlow's IAM credentials

---

## Next Session: Session 3 — BigCapital Config
- [ ] First login at https://webapp-production-1185.up.railway.app
- [ ] Set up Varshyl Inc organization profile
- [ ] Configure chart of accounts (construction-specific)
- [ ] Set up fiscal year and currency (USD)
- [ ] Create first project / customer
- [ ] Add MAIL_PASSWORD env var for email confirmations
