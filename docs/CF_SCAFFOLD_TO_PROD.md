# Cloudflare Pages — scaffold to prod (reference card)

House pattern used for **thecognitionfactory.com** and **johnhekmati.com**.  
Goal: `git push origin main` → live site, with sane cache and custom domain.

---

## Mental model

```text
GitHub repo (source of truth)
    │  push main
    ▼
GitHub Actions  ──uses──►  CLOUDFLARE_API_TOKEN
                           CLOUDFLARE_ACCOUNT_ID
    │
    ▼
wrangler pages deploy  →  Pages project (e.g. johnhekmati-com)
    │
    ▼
*.pages.dev  (+ custom domain when attached)
```

**Not** GitHub Pages for these sites (TCF never used it for prod).

---

## One-time setup

### 1. Repo
```powershell
cd C:\Grok\<site>
git init -b main   # if needed
# …commit…
gh repo create <name> --public --source=. --remote=origin --push
```
Use GitHub **noreply** commit email if “private email” blocks push.

### 2. Cloudflare API secrets (values are write-only on GitHub)
Dashboard: **My Profile → API Tokens** (create/copy) · Account home → **Account ID**.

```powershell
gh secret set CLOUDFLARE_ACCOUNT_ID -R <owner>/<repo>
gh secret set CLOUDFLARE_API_TOKEN  -R <owner>/<repo>
gh secret list -R <owner>/<repo>   # names only — spelling CLOUDFLARE not CLOUFLARE
```

Token needs **Account · Cloudflare Pages · Edit** (+ Account Read as required).

### 3. Deploy workflow (static site)
`.github/workflows/deploy.yml` — pattern:

1. `actions/checkout`
2. `actions/setup-node` (optional if only npx wrangler)
3. **Create project if missing**  
   `wrangler pages project create <project-name> --production-branch=main`  
   (or list + create)
4. **Deploy**  
   `npx wrangler@4 pages deploy . --project-name=<project-name> --branch=main --commit-dirty=true`

TCF extras (only if needed): `npm ci` + build step; separate Worker deploy.

### 4. Custom domain
- Zone for the domain must be on the **same** Cloudflare account.
- API (idempotent): `POST /accounts/{id}/pages/projects/{project}/domains` with `{"name":"example.com"}`  
  (house: `attach-domain.yml` for apex + `www`)
- Or dashboard: **Workers & Pages → project → Custom domains**.
- Wait for cert **pending → active**. Apex needs CF CNAME flattening / auto records.

### 5. Cache (`_headers` on Pages)
Overwrite-in-place files must **not** use year-long edge TTL.

| Path | Suggested |
|------|-----------|
| `/` (HTML) | `max-age=300, must-revalidate` |
| `/css/*`, `/assets/*` | `max-age=3600, must-revalidate` |
| Fingerprinted `/js/*` only | long + `immutable` optional |

File: repo-root **`_headers`** (Cloudflare Pages format). Deploy with the site.

---

## Day-to-day

```powershell
git add -A
git commit -m "…"
git push origin main
gh run list -R <owner>/<repo> --limit 3
# open *.pages.dev or custom domain after success
```

Hard-refresh after HTML/CSS changes; cache windows above bound staleness.

---

## Checklist (new static site)

- [ ] Public (or private) GitHub repo  
- [ ] Secrets: `CLOUDFLARE_API_TOKEN`, `CLOUDFLARE_ACCOUNT_ID` (correct spelling)  
- [ ] `deploy.yml` with create-if-missing + `pages deploy`  
- [ ] First Action green → `https://<project>.pages.dev`  
- [ ] Domain attached (apex + www if wanted)  
- [ ] `_headers` cache + security  
- [ ] No conflicting GitHub Pages CNAME if CF owns the domain  

---

## Gotchas

| Symptom | Fix |
|---------|-----|
| “project does not exist” | create step or dashboard project |
| Secrets “can’t pull values” | recreate from CF dashboard; GH is write-only |
| Typo `CLOUFLARE_*` | delete; workflow reads `CLOUDFLARE_*` only |
| Old HTML after deploy | shorter HTML TTL + hard refresh; purge CF cache if needed |
| Apex NXDOMAIN | domain attach + DNS in zone; wait for cert |
| Email privacy blocks push | amend author to `*@users.noreply.github.com` |

---

## Reference implementations

| Site | Path | Project |
|------|------|---------|
| TCF product | `C:\Grok\tcf-site` | `the-cognition-factory` |
| Personal | `C:\Grok\johnhekmati.com` | `johnhekmati-com` |

Last densified: 2026-07-13.
