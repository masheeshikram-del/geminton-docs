# Geminton documentation

## Public privacy policy (GitHub Pages — Option B)

The files **`privacy-policy.md`**, **`privacy-policy-plain.txt`**, and the landing page **`index.md`** can be published with **GitHub Pages** from this repository’s **`/docs`** folder.

1. Push this repo to GitHub (public or private per your plan; Pages on private repos may require a paid GitHub tier).
2. On GitHub: **Settings → Pages**.
3. **Build and deployment:** Source **Deploy from a branch**; Branch **`main`** (or your default), folder **`/docs`**.
4. After the first build (a minute or two), the site is available at:
   - **`https://<username>.github.io/<repository>/`** — home (`index.md`)
   - **`https://<username>.github.io/<repository>/privacy-policy.html`** — policy (use in Play Console / App Store)
   - **`https://<username>.github.io/<repository>/privacy-policy-plain.txt`** — plain text

Jekyll is configured via **`_config.yml`**. Internal guides (`FUNCTIONAL.md`, `TECHNICAL.md`, etc.) are **excluded** from the generated site but remain in the repo for developers.

If the policy changes, edit **`privacy-policy.md`** and **`privacy-policy-plain.txt`**, set the same **Last updated** date on both, commit, and push; the site updates on the next build.

---

| Document | Audience | Purpose |
|----------|----------|---------|
| **[FUNCTIONAL.md](./FUNCTIONAL.md)** | Traders, QA, developers | **Single** plain-language guide to what the app does (same story for users and product); technical build detail is in TECHNICAL.md |
| **In-app Help** | End users | **`assets/help/user_guide.md`** — keep aligned with FUNCTIONAL.md (see [AGENTS.md](../lib/theme/AGENTS.md) maintenance) |
| **[TECHNICAL.md](./TECHNICAL.md)** | Developers | Architecture, stack, folders, data & services, **Mermaid flow diagrams** (§6) |
| **[AGENTS.md](../lib/theme/AGENTS.md)** | AI assistants + devs (quick rules) | Cursor/agent context, constraints, field-change checklist |

**Maintenance:** When you change product behavior or architecture, update the relevant doc(s) above and keep **`lib/theme/AGENTS.md`** in sync for anything agents must follow. See the **Documentation maintenance** section there.

**Note:** The file is **`AGENTS.md`** (all caps). GitHub URLs are **case-sensitive**; `Agents.md` will 404.
