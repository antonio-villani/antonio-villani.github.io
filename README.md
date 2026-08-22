# antoniovillani.eu — personal academic website

Static HTML. No framework, no build step, no JavaScript. Editing a file and pushing
is the entire deployment process.

## ⚠️ This directory is public

Everything in this folder is served on the open web. **Never copy anything into it from
elsewhere in `Job-Market/`** — that folder holds referee names and addresses, the full
list of places applied to, interview outcomes and offer terms. Private notes about the
website live one level up, in `Package/Website/`, which is outside this repo.

## Files

| File | What it is |
|---|---|
| `index.html` | Homepage — bio, job market paper, work in progress |
| `research.html` | Full paper list, abstracts expanded |
| `teaching.html` | Teaching experience |
| `cv.html` | HTML mirror of the CV PDF |
| `contact.html` | Email, address, profile links |
| `404.html` | Not-found page |
| `css/style.css` | The only stylesheet |
| `files/` | PDFs — **stable filenames, overwritten in place** |
| `assets/` | Photo and favicon |
| `CNAME` | Custom domain. Do not delete — GitHub Pages reads this file |
| `sitemap.xml` | Update `lastmod` when content changes materially |

## Updating

```bash
cd "Package/Website/site"
git add -A && git commit -m "Update JMP abstract" && git push
```

Live in under a minute.

- Homepage text, the JMP block → `index.html`
- Full paper list → `research.html`
- New CV → **overwrite** `files/villani_cv.pdf` (keep the filename)
- New JMP → **overwrite** `files/villani_jmp.pdf` (keep the filename)

## Why the PDF filenames never change

Committees save links. A link sent in November must still work in March, so the served
filenames are stable and overwritten in place. The *dated* record of what was actually
sent to whom lives in `Package/CV/` and `Package/JMP/` as
`YYYY-MM-DD_<artefact>_v<N>.pdf`, per the project convention. Git history here is a
second, automatic record.

## Adding a paper

`research.html` contains a commented-out `Working Papers` block to copy. Order is
Job Market Paper → Working Papers → Work in Progress. Abstracts use native
`<details>`/`<summary>` — no JavaScript. The JMP abstract carries `open`; the rest do not.

## SEO invariants — do not break these

- One `<h1>` per page, containing the full name on the homepage.
- `<link rel="canonical">` on every page, absolute, pointing at `https://antoniovillani.eu/…`.
- The JSON-LD `Person` block in `index.html` — add profile URLs to `sameAs` as they exist
  (Google Scholar, LinkedIn, X, ORCID, RePEc, EJME).
- Keep PDFs text-based, never scanned images, so their contents are indexable.
- Add any new page to `sitemap.xml`.
