# johnhekmati.com

Personal site for **John Hekmati** — identity and path. Product platform: [thecognitionfactory.com](https://thecognitionfactory.com).

| | |
|--|--|
| **Path** | `C:\Grok\johnhekmati.com` |
| **GitHub** | `johnhekmati/johnhekmati.com` |
| **Live** | Cloudflare Pages project `johnhekmati-com` → custom domain when DNS attached |
| **Deploy** | Push `main` → Actions → `wrangler pages deploy` (same pattern as TCF) |

## Stack

- Static HTML + CSS (no build step)
- Deploy: Cloudflare Pages via `.github/workflows/deploy.yml`
- Secrets: `CLOUDFLARE_API_TOKEN`, `CLOUDFLARE_ACCOUNT_ID` (repo Actions secrets)

## Local preview

```powershell
cd C:\Grok\johnhekmati.com
npx --yes serve
```

## Portrait

Local copy of the Architect headshot used on The Cognition Factory site. Re-sync if the public photo changes.

## Presence doctrine

Thin foundation only: LinkedIn + this site. No Substack content machine. Services language only when factory capacity can back it.
