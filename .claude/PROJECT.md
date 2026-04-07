# interluud — Project Context

> Paste this file's contents at the start of any new Claude conversation to restore full project context instantly.

---

## What is interluud?

A relationship transition coaching practice for **high-achieving professionals** navigating divorce, separation, or breakup. The brand positions coaching as a strategic, structured process — not just emotional support. Think: a brilliant friend who also ran a company.

**Coach:** Gabrielle San Nicola
**Booking link:** https://meetings-na2.hubspot.com/gabrielle-san-nicola
**Domain:** interluud.com

---

## Services

1. **Divorce & Separation** — From decision to the other side. Process, strategy, emotional clarity running in parallel.
2. **Breakup Recovery** — Structured support for relationships that ended but won't stop echoing.
3. **Co-parenting Strategy** — Practical frameworks for navigating shared parenthood after separation.

---

## Tech Stack & Hosting

| What | Where | Notes |
|------|-------|-------|
| Main site | Vercel (free) | Static HTML files, deploys from GitHub |
| Domain | interluud.com | Moving DNS away from Squarespace to Vercel |
| Blog | Ghost (blog.interluud.com) | $9/mo hosted plan, newsletter built in |
| Email forwarding | Cloudflare | hello@interluud.com → Gmail, free |
| Booking | HubSpot | https://meetings-na2.hubspot.com/gabrielle-san-nicola |

### DNS setup (once done)
- `interluud.com` A record → Vercel's IP
- `www` CNAME → cname.vercel-dns.com
- `blog` CNAME → Ghost's URL
- Cloudflare handles nameservers for everything

---

## File Structure (GitHub repo)

```
interluud/               ← GitHub repo root
├── index.html           ← Homepage
├── about/
│   └── index.html       ← Who We Are
├── services/
│   └── index.html       ← Services
├── faq/
│   └── index.html       ← FAQs
├── blog/
│   └── index.html       ← Blog landing (links to Ghost)
└── images/              ← Upload compressed photos here
    └── (photos go here)
```

### How Vercel serving works
- `index.html` → interluud.com/
- `about/index.html` → interluud.com/about
- `services/index.html` → interluud.com/services
- etc.

### How to edit content
1. Go to GitHub repo → click the file → click pencil icon → edit → commit
2. Vercel redeploys automatically in ~30 seconds
3. For local editing: use VS Code (free), or TextEdit in Plain Text mode

### How to add images
1. Compress at squoosh.app first (aim for <300kb)
2. Upload to `images/` folder in GitHub repo
3. Reference as `<img src="/images/filename.jpg">`

---

## Pages still needing Gabrielle's real content

- `about/index.html` — Replace placeholder bio, background, credentials
- `services/index.html` — Add real pricing/package details if desired
- `faq/index.html` — Review/update FAQ answers to match actual practice
- All pages — Replace any `[placeholder]` text
- All pages — Add real photography via `/images/` folder

---

## Decisions made & why

- **No Squarespace** — Template constraints too limiting for this design. Moved to Vercel static hosting.
- **No Webflow** — Ghost + Vercel is simpler and cheaper for this use case.
- **Ghost for blog** — Best writing experience, newsletter built in, clean design, custom domain, $9/mo.
- **Cloudflare for DNS** — Free email forwarding is the main win. Also better DNS management than most registrars.
- **No photography in hero** — Typographic hero is more distinctive and avoids stock photo genericness.
- **Cormorant + DM Sans** — Editorial serif for emotional weight, geometric sans for precision. Matches the "strategic + human" brand positioning.
