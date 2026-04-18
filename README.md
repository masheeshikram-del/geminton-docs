# Geminton — public privacy site (GitHub Pages)

This folder contains **only** what should appear in the public **[geminton-docs](https://github.com/masheeshikram-del/geminton-docs)** repository. Do **not** add `FUNCTIONAL.md`, `TECHNICAL.md`, or agent docs here.

## Publish to `geminton-docs`

1. Copy **all files in this folder** (including `README.md` if you want it on GitHub; it is not part of the Jekyll site unless you remove it from copy) into the **root** of `geminton-docs`. Typical set:
   - `_config.yml`
   - `index.md`
   - `privacy-policy.md`
   - `privacy-policy-plain.txt`
2. **GitHub Pages:** Settings → Pages → Branch **`main`**, folder **`/ (root)`** (not `/docs`).
3. Live URLs (replace with your username/repo if different):
   - `https://masheeshikram-del.github.io/geminton-docs/`
   - `https://masheeshikram-del.github.io/geminton-docs/privacy-policy.html`
   - `https://masheeshikram-del.github.io/geminton-docs/privacy-policy-plain.txt`

## Maintenance

Edit **`privacy-policy.md`** and **`privacy-policy-plain.txt`** in this folder; keep **Last updated** identical on both. Commit in the **app** repo, then re-copy to `geminton-docs` and push.

See also **`docs/README.md`** in the app repo for the full documentation index.
