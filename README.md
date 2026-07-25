# johnhekmati.com

Personal site for **John Hekmati** — identity and path.

| | |
|--|--|
| **Path** | `C:\Grok\johnhekmati.com` |
| **GitHub** | `johnhekmati/johnhekmati.com` |
| **Live** | Cloudflare Pages project `johnhekmati-com` → custom domain when DNS attached |
| **Deploy** | Push `main` → Actions → `wrangler pages deploy` (same pattern as TCF) |

## Stack

- Static HTML + CSS + small inline reveal JS (no build step)
- Deploy: Cloudflare Pages via `.github/workflows/deploy.yml`
- Secrets: `CLOUDFLARE_API_TOKEN`, `CLOUDFLARE_ACCOUNT_ID` (repo Actions secrets)

## Local preview

```powershell
cd C:\Grok\johnhekmati.com
npx --yes serve
```

## Portrait

Local copy of the Architect headshot. Re-sync if the public photo changes.

## Presence doctrine

Thin foundation only: LinkedIn + this site. No Substack content machine. Services language only when factory capacity can back it.

**Page job:** real person under real load — martial formation as life anchor, family, hard domains — then the worlds he builds (Hekmati Consulting Group, The Cognition Factory, Form & Frame Design, Professional MMA Institute). Visual: elevated charcoal personal palette with steel + warm-metal life accents (not TCF electric/plasma, not FFD paper/teal, not PMMAI gold). Contact first. Faith stays private. Not a second product or consulting site — those have their own homes.

**Contact:** `hello@johnhekmati.com` (Proton custom domain; catch-all OK). Product form remains on TCF. Consulting routing points to HCG.

## Ops

- Cache / security headers: `_headers` (HTML 300s · css/assets 3600s — same idea as TCF)
- CF scaffold-to-prod card: [`docs/CF_SCAFFOLD_TO_PROD.md`](docs/CF_SCAFFOLD_TO_PROD.md)
