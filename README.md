# Geminton — public privacy site (GitHub Pages)

This folder contains **only** what should appear in the public **[geminton-docs](https://github.com/masheeshikram-del/geminton-docs)** repository. Do **not** add `FUNCTIONAL.md`, `TECHNICAL.md`, or agent docs here.

The site is **static** (`.nojekyll`): GitHub serves `index.html` and `privacy-policy.html` **without** running Jekyll, so you avoid build failures.

## Files to copy to `geminton-docs` (repo root)

| File | Purpose |
|------|---------|
| `.nojekyll` | Tells GitHub Pages not to use Jekyll |
| `index.html` | Home page |
| `privacy-policy.html` | **Use this URL in Play / App Store** |
| `privacy-policy-plain.txt` | Plain-text mirror |
| `privacy-policy.md` | Optional; same wording, for GitHub preview / diffs |
| `README.md` | This file (optional on the public repo) |

## GitHub settings (if you see 404)

1. Repo: **Settings → Pages**.
2. **Build and deployment:** source **Deploy from a branch** (not “GitHub Actions” only with no workflow).
3. Branch: **`main`**, folder **`/ (root)`** — **not** `/docs` unless your files live in a `docs/` subfolder (they should be at the **root** of `geminton-docs`).
4. Wait **5–10 minutes** after the first successful deploy.
5. Open **Actions** (or **Environments → github-pages**) and confirm the latest **pages build** succeeded. If it failed, open the log (often a wrong **Publishing** path).

## Live URLs

- `https://masheeshikram-del.github.io/geminton-docs/`
- `https://masheeshikram-del.github.io/geminton-docs/privacy-policy.html`
- `https://masheeshikram-del.github.io/geminton-docs/privacy-policy-plain.txt`

## Maintenance

When the policy changes:

1. Edit **`privacy-policy.md`**, **`privacy-policy-plain.txt`**, and **`privacy-policy.html`** so they match (same **Last updated** on all).
2. Commit in the **app** repo.
3. Copy this folder to `geminton-docs`, commit, and push.

See **`docs/README.md`** in the app repo for the full documentation index.
