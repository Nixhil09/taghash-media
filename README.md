# Taghash Media — site

Static site. No build step. Deploy this folder as-is.

## Deploy (Vercel)
- Framework preset: **Other**. Build command: none. Output directory: `.` (this folder is the root).
- `vercel.json` enables clean URLs (`/automation`, not `/automation.html`), redirects `/home` and `/service`, and sets security + content-type headers.
- Production domain assumed: `https://taghashmedia.com`. If you use `www` or another domain, find-and-replace `https://taghashmedia.com` across `*.html`, `sitemap.xml`, `robots.txt`, `llms.txt`, `llms-full.txt`, `*.md`.

## Structure
- `index.html`, `services.html`, `work.html`, `approach.html`, `about.html`, `contact.html` — main pages
- `performance-marketing.html`, `automation.html`, `geo-seo.html`, `content-pr.html`, `ux-web.html`, `engineering.html` — service pages
- `Taghash Footer.dc.html`, `Taghash Survey.dc.html` — shared components loaded by every page (footer + survey popup). Keep the filenames exactly; they're served with `noindex`.
- `support.js` — runtime that renders the pages. Required.
- `uploads/` — logo, showreel, generated artwork (`uploads/art/`)
- SEO / LLM: `sitemap.xml`, `robots.txt`, `llms.txt`, `llms-full.txt`, and a `.md` twin of every page. Each HTML page has title, meta description, canonical, Open Graph, JSON-LD (Organization, WebSite, Service, FAQPage, BreadcrumbList) and a `<noscript>` text version.

## Case studies
- One page per client: `case-<slug>.html` → `/case-<slug>` (e.g. `/case-bimmerplug`). Linked from Home, Work, Services and each case's "More work" row. All listed in `sitemap.xml` and `llms.txt`.
- Banners live in `uploads/cases/`.

## Survey → contact
The survey popup opens from any `href="#survey"` link or the floating "Scope your project" pill. Answers are saved to `localStorage` (`tgSurvey`) and prefilled on `/contact?from=survey`. The contact form's "Send the brief" is front-end only — wire it to a form backend (Formspree, Resend, HubSpot, a Vercel function) before launch.

## To do before launch
- Case study numbers, briefs and "The win" copy are placeholders — confirm with each client.
- Footer social links still point to /contact.
- Team portraits (Bikram, Manjit, Ayushi, Sonali) and the About photo wall are placeholders. Founder photos live in `uploads/team/` (Part 2).
- Newsletter inputs are not wired to a provider.
- After deploy: submit `sitemap.xml` in Google Search Console and Bing Webmaster Tools.
