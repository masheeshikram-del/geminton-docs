# Plan iteration: documentation + in-app Help

**Status:** Implemented — `Help` drawer item, `HelpScreen`, `assets/help/user_guide.md`, unified `docs/FUNCTIONAL.md`, `flutter_markdown`, navigation indices 6/7.

## Unified functional doc (no separate “Part 2”)

**Decision:** **`docs/FUNCTIONAL.md` should be one document** that serves **both** end users and developers for *what the product does*.

- **Same content, one voice:** Write it **trader-first** (plain language, screen-by-screen, “you”). Developers and QA use that same file as the **functional source of truth**—they do not need a parallel “technical functional” section inside the same file.
- **Where deep implementation lives:** Architecture, folders, Hive, services map, Mermaid flows → stay in **[`TECHNICAL.md`](TECHNICAL.md)**. Agent rules and checklists → **[`AGENTS.md`](../lib/theme/AGENTS.md)**.

So: **functional spec ≈ user-understandable description of behavior.** If a detail is too internal for a trader (e.g. exact certificate column limits in backup vs label export), phrase it in **plain English** (“Backups try to keep all your certificates; label files for printing may list up to three types”) or add a short **Note for advanced users**—avoid a whole second part aimed only at devs.

**Optional:** A tiny **“On this page”** list at the top linking to major headings—still one body of content, not Part 1 / Part 2.

---

## In-app Help

- **`assets/help/user_guide.md`** can be the **same text as `FUNCTIONAL.md`**, or a **shorter extract** if the full file is too long on a phone. Prefer **one master** (`FUNCTIONAL.md`) and sync/copy to the asset when building or when Help content changes—so you are not maintaining two different stories.

---

## Maintenance ([`AGENTS.md`](../lib/theme/AGENTS.md))

When behavior or labels change:

1. Update **`FUNCTIONAL.md`** (single unified doc).
2. Sync **`assets/help/user_guide.md`** if it is not generated from the same file automatically.
3. Update **`TECHNICAL.md`** only when architecture/integration changes; **`AGENTS.md`** when agent policies change.

---

## Implementation order (when executing)

1. **Rewrite/expand [`FUNCTIONAL.md`](FUNCTIONAL.md)** into the unified trader-readable functional spec (merge old content into plain-language sections; remove duplicate “dev-only” functional bullets where they repeat TECHNICAL.md).
2. Add **`assets/help/user_guide.md`** (copy or trim from `FUNCTIONAL.md`).
3. Implement **Help** screen + `flutter_markdown` + `pubspec` assets.
4. Drawer: **Help** before **About**; stack indices **6 / 7** ([`navigation_drawer.dart`](../lib/navigation_drawer.dart), [`main_navigation_scaffold.dart`](../lib/main_navigation_scaffold.dart)).
5. Update [`docs/README.md`](README.md) to describe **one** functional doc + link to TECHNICAL for code-level detail.

---

## Help UI (unchanged)

- `HelpScreen` + `flutter_markdown` + bundled Markdown.
- Indices: **6 = Help**, **7 = About**.
