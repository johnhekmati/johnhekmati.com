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

**Page job:** real person under real load — martial formation as life anchor, family, hard domains — then the worlds he builds (Hekmati Consulting Group, The Cognition Factory, Form & Frame Design, Professional MMA Institute, Star Schema Publishing). Visual: elevated charcoal personal palette with steel + warm-metal life accents (not TCF electric/plasma, not FFD paper/teal, not PMMAI gold). Contact first. Faith stays private. Not a second product or consulting site — those have their own homes.

**Backlink placement:** this page is the hub of the personal identity graph — every property carries `rel="me"` and appears in the `Person` JSON-LD `sameAs`. Ventures go in **Builds**; `hekmatifamily.com` stays out of Builds by doctrine (it is a private family porch, not a venture) and is linked once from the Home life block and once from the footer.

## Layout invariant

Every band — nav, hero, sections, footer — uses `.wrap` for its horizontal spine, and **nothing overrides `.wrap`'s width or margin**. Breaking this is what put the hero copy ~300px out of alignment with the nav before 2026-08-05. Section text blocks share `--measure` (42rem); Builds rows are deliberately full-spine because they are interactive rows, not prose.

**Contact:** `hello@johnhekmati.com` (Proton custom domain; catch-all OK). Product form remains on TCF. Consulting routing points to HCG.

## Ops

- Cache / security headers: `_headers` (HTML 300s · css/assets 3600s — same idea as TCF)
- CF scaffold-to-prod card: [`docs/CF_SCAFFOLD_TO_PROD.md`](docs/CF_SCAFFOLD_TO_PROD.md)
