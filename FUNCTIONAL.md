# Geminton — how the app works

**Who this is for:** Gem traders using the app day to day—and anyone (including developers) who needs a plain-language description of what Geminton does. For **how the code is organized**, see [TECHNICAL.md](./TECHNICAL.md).

---

## On this page

- [What is Geminton?](#what-is-geminton)
- [One “stone” in the app](#one-stone-in-the-app)
- [Main menu (side drawer)](#main-menu-side-drawer)
- [Gem Library](#gem-library)
- [Add Gem](#add-gem)
- [Open a stone: detail and edit](#open-a-stone-detail-and-edit)
- [Filters](#filters)
- [Analytics](#analytics)
- [Message templates and sharing](#message-templates-and-sharing)
- [Import Data](#import-data)
- [Configure](#configure)
- [Exhibition (Salesmen)](#exhibition-salesmen)
- [Backup and safety](#backup-and-safety)
- [Help](#help)
- [About](#about)
- [Free vs Pro](#free-vs-pro)
- [Good to know](#good-to-know)
- [Related documents](#related-documents)

---

## What is Geminton?

Geminton is a **phone app for gemstone traders**. You keep each stone (or line item) as a **record** on your device: photos and videos, certificates, what you paid, what you’re asking, sale and buyer payment details, notes, and more. You can **search and filter** your stock, see **summaries and money-style analytics**, **export** data for labels or trade shows, **import** spreadsheets or a full backup, and **build messages** (e.g. for WhatsApp or WeChat) from templates.

Your data is **stored on your phone first**. You can turn on **backup** so copies go to the cloud (for example Google on Android), depending on how you set things up.

---

## One stone in the app

Each saved item is a **gem record**. It can include:

- **Basics:** type of gem, weight (carat), color, clarity, cut, origin, treatment, special effects (phenomena), etc.
- **Price and status:** asking price, currency, whether it’s available, sold, etc.
- **Certificates:** You can attach **more than one** certificate (lab name, number, link, notes, pictures of the cert).
- **Size:** measurements.
- **Buying:** purchase price, date, supplier, payment info, etc.
- **Selling and buyer:** sale price, buyer payment status, due dates, etc. **The app does not copy your asking price into buyer fields for you**—you fill those when you’re ready.
- **Notes** and extra text.
- **Photos and videos** of the stone.
- **Custom fields** you define in Configure (extra labels and values for your business).

---

## Main menu (side drawer)

Open the **menu** (☰) to move around the app.

| Menu item | What it’s for |
|-----------|----------------|
| **Gem Library** | Your list of all stones. |
| **Add Gem** | Start a new record (always starts with **options**: certificate upload/scan, or blank form). |
| **Analytics** | Charts and totals: overview, aging, money, payments. |
| **Message Templates** | Saved message layouts with placeholders for stone data. *Pro — badge on menu if you’re on Free.* |
| **Import Data** | Bring in Excel files or a **backup ZIP** from a computer or cloud. *Pro — badge if Free.* |
| **Configure** | Pinned fields, what’s visible, dropdown lists, sections, custom fields, export options, backup settings. *Pro — badge if Free.* |
| **Exhibition (Salesmen)** | Export/import formatted for **trade show** workflows; QR where the app supports it. |
| **Help** | This guide inside the app. |
| **About** | App name, version, short feature list. |

---

## Gem Library

**What this is for:** See everything you’ve saved, find a stone quickly, and open it.

**What you do here:**

1. Scroll the list or use **search** if available.
2. Use **filters** (simple or advanced) to narrow the list—for example by gem type, origin, or payment status.
3. **Tap a row** to open that stone’s **detail** screen.
4. From the library you may also **export for labels** (print-style spreadsheet) or start **Add Gem**, depending on buttons shown.

**Good to know:** Some filters can highlight **overdue buyer payments** so you can chase payments faster.

---

## Add Gem

**What this is for:** Create a new stone record.

**What you do here:**

1. Tap **Add Gem**. You always see **Add Gem Options** first—not the full form immediately.
2. On **Add Gem Options**, you might:
   - Take or choose a **photo of a certificate** so the app can suggest fields (accuracy depends on the image and settings).
   - Go **straight to a blank** new stone with **Manual Entry**.
3. You then land on the **big form** (add/edit screen). **Pinned** fields stay visible at the top; other fields are grouped in **sections** you can expand or collapse.
4. Add **photos/videos**, certificates, prices, purchase info, etc.
5. **Save** when done. The record is stored **on your device**.

**Good to know:** Buyer/sale fields are **empty by default**; they are **not** auto-filled from your asking price.

**Duplicate warning:** When you save a **new** record, the app checks whether a similar stone already exists (same gem type, carat weight, record name, and first certificate). If a match is found you see a prompt: **View Existing**, **Save Anyway**, or **Cancel**.

---

## Open a stone: detail and edit

**Detail screen:** After you tap a stone in the library, you see a **read-friendly** view: main facts, media, certificates, etc.

**Edit:** Use **Edit** (or equivalent) to open the **same long form** as Add Gem, with all fields for that record.

**Sharing / messages:** From the right place in the flow you can build text from a **template** and send or copy it (e.g. to WhatsApp or WeChat).

---

## Filters

**What this is for:** Cut down a long library list to stones that match rules you care about.

**What you do here:**

1. Open **basic** or **advanced** filter tools from the library (exact buttons depend on your app version).
2. Build conditions (e.g. gem type, price range, availability).
3. You can **save** a filter to reuse later.

---

## Analytics

**What this is for:** Understand your stock and money at a glance—using **dates** you choose on each tab where it applies.

**Tabs (typical):**

| Tab | Plain meaning |
|-----|----------------|
| **Overview** | High-level picture of your inventory and activity for the period you pick. |
| **Stock Aging** | How long stones have been in stock / not sold (depending on your data). |
| **Capital & Profit** | Money-style views: purchase cost vs sale, etc., where the data exists. |
| **Payments** | Buyer payments, dues, and related summaries. |

**Good to know:** Where both exist, analytics **prefer sold price over asking price** for money math. Empty buyer/sale fields are **skipped** so they don’t fake numbers. **Currency** on screen may be converted using **online rates** when you open Analytics (refreshed about daily)—good for a **rough** view, not formal accounting.

---

## Message templates and sharing

**What this is for:** Write **reusable messages** with gaps like “gem type” or “price” filled in from a stone’s data—handy for WhatsApp or WeChat style sharing.

**What you do here:**

1. Open **Message Templates** (Pro).
2. Create or edit a template; the app offers **placeholders** for standard and **custom** fields.
3. When you **generate content** from a stone, pick a template and share or copy the result.

---

## Import Data

**What this is for:** Bring data **into** Geminton from outside.

**Two common cases:**

1. **Excel file (.xlsx)** — For migration or bulk updates. You **map columns** to fields in the app. **Pictures are not restored** from a plain Excel file by themselves.
2. **ZIP backup** — A **full backup** from Geminton (or compatible export) usually contains a spreadsheet **and** media files. Restoring from that ZIP can put **photos** back in the right records.

**Exhibition:** If you use **exhibition** packages, import paths for that format may appear here or under **Exhibition**—follow on-screen steps.

### Duplicate detection during import

Geminton builds a **fingerprint** from each row (gem type, carat weight, record name, first certificate type + number). If the fingerprint matches an existing record the row **updates** that record instead of creating a duplicate — even when the ID column is missing or the IDs differ. The import preview shows how many rows are new, matched by ID, or matched by fingerprint.

---

## Configure

**What this is for:** Shape how the app **looks and behaves** for data entry and exports—without writing code.

**Typical things you can change:**

- Which fields are **pinned** on the add/edit screen.
- Which system fields are **visible** on the form.
- **Dropdown** lists (e.g. colors, origins) and **defaults**.
- **Sections** and **order** of fields.
- **Custom fields** (your own labels and types).
- What goes into **label export** (for printing) vs **exhibition** export—each can have its own visibility.
- **Backup:** sign-in (e.g. Google on Android), how often **automatic** backup runs, optional paths.

*Pro required for Configure on Free plans—check the menu badge.*

---

## Exhibition (Salesmen)

**What this is for:** Work in **trade-show** mode: export a package others can use, or import one you received; **QR** may be used to pass files or links where supported.

**What you do here:** Follow the buttons on the Exhibition screen for **export** / **import** and any QR flow. Which **fields** appear in those files is controlled partly from **Configure → exhibition visibility**.

---

## Backup and safety

**What this is for:** Not lose everything if the phone is lost or damaged.

**What you do here:**

- Turn on **automatic** backup in Configure (if you have access) and sign in where asked (e.g. Google on Android).
- Run a **manual** backup when you want an extra snapshot.

**What a backup usually contains:** A **ZIP** with a **spreadsheet of your records** plus **media files** linked by filename. **Backups try to keep all your certificate columns** in the spreadsheet. **Label files for printing** may list **up to three** certificate types for simplicity—that limit does **not** mean you only own three certs in the app.

---

## Help

**What this is for:** Reread this guide **inside the app** without leaving Geminton.

The in-app text is kept in sync with this document as much as possible; the **full** copy with links may also live in your project **docs** folder on GitHub or your computer.

---

## About

**What this is for:** See **app name**, **version**, and a short **feature list**.

---

## Free vs Pro

- **Free:** Use the **core library**, add and edit records, and **fill in values** on the add/edit screen (including values for custom fields **if those fields already exist**). **Configure** on Free is **view-only**—you cannot fully edit layout, create or edit **custom field definitions**, sections/pinning, or most backup options; that requires **Pro**.
- **Pro:** Full **Configure** editing and the other features that show a **Pro** badge on the menu when you’re on Free—typically **Analytics**, **Message Templates**, **Import Data**, and often **automatic backup**, depending on version.

---

## Good to know

- **Certificate scan** tries to **read** a certificate image; always **check** the values before you rely on them.
- **Import/export** formats can differ: **backup ZIP** is the safest for **full** restore including photos.

---

## Related documents

- **[TECHNICAL.md](./TECHNICAL.md)** — Architecture, folders, services, flow diagrams (for developers).
- **[AGENTS.md](../lib/theme/AGENTS.md)** — Rules for AI-assisted coding in this repo.

---

*Update this file when behavior, labels, or navigation change. If you use in-app Help, update **`assets/help/user_guide.md`** to match (see [AGENTS.md](../lib/theme/AGENTS.md)).*
