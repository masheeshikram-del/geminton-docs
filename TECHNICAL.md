# Geminton — Technical overview

**Stack:** Flutter (Dart SDK per `pubspec.yaml`)  
**Package name:** `geminton` (see `pubspec.yaml`)

**Audience:** Developers joining the project or implementing features.

---

## 1. Repository layout (high level)

```
lib/
  main.dart                    # App entry, service init, auto-backup kickoff
  main_navigation_scaffold.dart
  navigation_drawer.dart
  screens/                     # All feature screens
  services/                    # Domain-grouped services (see §4)
  models/                      # GemRecord, Certificate, templates, filters, etc.
  widgets/                     # Shared UI (filters, certificate dialog, …)
  theme/                       # app_theme.dart, AGENTS.md (AI context)
  utils/
docs/                          # This folder — functional + technical specs
```

---

## 2. Runtime initialization (`main.dart`)

Typical startup:

- `WidgetsFlutterBinding.ensureInitialized()`
- `GemRecordService.init()` — Hive Flutter + opens box for records
- `ApprovalHistoryService.init()` — Hive adapters for approval history
- `AppEntitlementsService.init()`
- `FileHandlerService.initializeListener()` — file intents when app already running
- Optional: `CloudBackupService.shouldAutoBackup()` → `performAutoBackup()` (not awaited)
- `runApp(MyApp())`

---

## 3. Data & persistence

### 3.1 Gem records

- **Storage:** Hive box `gemRecords`; each value is a **JSON string** (`jsonEncode` / `jsonDecode` of `GemRecord`).
- **Model:** `lib/models/gem_record.dart` — **canonical** shape for saved data; `toJson` / `fromJson` migrations must stay backward compatible when agreed.

### 3.2 Approval history

- **Storage:** Hive **type adapters** with `@HiveType` / `@HiveField` in `lib/models/approval_history.dart`.
- **Constraint:** Never reuse or reorder `@HiveField` indices; add new fields with the next index only.

### 3.3 Other persisted state

- **SharedPreferences:** Field visibility, export visibility, templates, currency rate cache, exhibition metadata, entitlements-related flags, etc. (see respective services).

---

## 4. Services map (`lib/services/`)

| Folder | Responsibility |
|--------|----------------|
| `records/` | `GemRecordService`, `GemDataService`, validation, `ApprovalHistoryService`, **`GemDuplicateService`** (fingerprint hash for dedup) |
| `field_config/` | Visibility, sections, order, custom fields, dropdowns, color grades integration |
| `certificate/` | `GemVisionService`, deterministic extraction v2, OCR, parsing, lab detection |
| `export/` | Label + exhibition export; `label_export_visibility_service`, `exhibition_visibility_service` |
| `import/` | Excel import, exhibition import |
| `backup/` | `CloudBackupService`, Google Drive, media backup, image compression |
| `filters/` | Saved filters, builder, application to queries |
| `messaging/` | `TemplateService`, `MessagingAppService` (open WhatsApp/WeChat) |
| `analytics/` | `AnalyticsSummaryBuilder`, `CurrencyConverterService` (Fawaz API + cache) |
| `ai/` | **Dormant** product AI (`ai_service`, insights services); do not change without explicit product request |

Root-level services (examples): `app_entitlements_service`, `file_handler_service`, `gem_color_grades_service`, `template_service` was moved under messaging — use `messaging/template_service.dart`.

---

## 5. Navigation & routing

- **Drawer-driven** shell: `MainNavigationScaffold` swaps body by index; **Add Gem** uses index `-1` and pushes `AddGemOptionsScreen`.
- **Deep links / file open:** `main.dart` + `FileHandlerService` for sharing files into import flows where implemented.

---

## 6. Flow diagrams (Mermaid)

These diagrams summarize **how control and data move** through the app. They are approximate—check the cited files for edge cases.

**Viewing:** GitHub renders Mermaid in markdown. In VS Code, use a Mermaid preview extension, or paste into [mermaid.live](https://mermaid.live).

### 6.1 Application startup

```mermaid
flowchart TD
  A["main()"] --> B["WidgetsFlutterBinding.ensureInitialized()"]
  B --> C["GemRecordService.init() — Hive + gemRecords box"]
  B --> D["ApprovalHistoryService.init()"]
  B --> E["AppEntitlementsService.init()"]
  B --> F["FileHandlerService.initializeListener()"]
  B --> G["CloudBackupService.shouldAutoBackup() → performAutoBackup() — fire-and-forget"]
  C --> H["runApp(MyApp)"]
  D --> H
  E --> H
  F --> H
  G --> H
```

### 6.2 Main shell: drawer → body

```mermaid
flowchart TD
  subgraph Shell["MainNavigationScaffold"]
    Drawer["AppNavigationDrawer"]
    Body["IndexedStack / body widget by _selectedIndex"]
  end
  Drawer -->|"index 0"| Lib["SavedGemsLibraryScreen"]
  Drawer -->|"index -1 (special)"| Add["Navigator.push → AddGemOptionsScreen"]
  Drawer -->|"1"| Ana["AnalyticsScreen"]
  Drawer -->|"2"| Tpl["TemplateManagerScreen"]
  Drawer -->|"3"| Imp["ImportExcelScreen"]
  Drawer -->|"4"| Cfg["ConfigureScreen"]
  Drawer -->|"5"| Exh["ExhibitionScreen"]
  Drawer -->|"6"| Hlp["HelpScreen"]
  Drawer -->|"7"| Abo["AboutScreen"]
```

*(Exact indices are defined in `main_navigation_scaffold.dart` / drawer—verify if you add menu items.)*

### 6.3 Add Gem → save record

```mermaid
sequenceDiagram
  participant Nav as MainNavigationScaffold
  participant GemOpt as AddGemOptionsScreen
  participant Vis as GemVisionService
  participant Inp as GemInputScreen
  participant Svc as GemRecordService
  participant HiveDB as Hive gemRecords
  Nav->>GemOpt: push Add Gem
  GemOpt->>Vis: certificate image analysis when used
  Vis-->>GemOpt: GemImageAnalysis prefilled fields
  GemOpt->>Inp: push with initial data or blank
  Inp->>Svc: saveRecord(record)
  Svc->>HiveDB: put id and jsonEncode toJson
```

### 6.4 Gem Library: load, filter, open detail

```mermaid
flowchart TD
  A["SavedGemsLibraryScreen"] --> B["GemRecordService.getAllRecords()"]
  B --> C["List GemRecord in memory"]
  C --> D{"Saved filters / FilterApplicationService?"}
  D --> E["Filtered list for UI"]
  E --> F["Tap row"]
  F --> G["Navigator → GemRecordDetailScreen"]
  G --> H["Edit → GemInputScreen"]
```

### 6.5 Configure → field visibility on form

```mermaid
flowchart LR
  subgraph Prefs["SharedPreferences"]
    K["Keys per field e.g. visibility_*"]
  end
  FVS["FieldVisibilityService"]
  CFG["ConfigureScreen — toggles"]
  INP["GemInputScreen — builds sections"]
  CFG <-->|read/write| FVS
  FVS <-->|prefs| Prefs
  INP -->|queries| FVS
```

### 6.6 Label export (high level)

```mermaid
flowchart TD
  A["SavedGemsLibraryScreen — user action"] --> B["LabelExportService"]
  B --> C["LabelExportVisibilityService — which columns"]
  B --> D["GemRecordService.getAllRecords or subset"]
  D --> E["Build CSV / Excel columns"]
  E --> F["Share / save file"]
```

### 6.7 Import: ZIP backup vs standalone Excel

```mermaid
flowchart TD
  Start["ImportExcelScreen / user picks file"] --> Kind{ZIP or .xlsx?}
  Kind -->|ZIP backup| Z["Archive extract — Excel + media folder"]
  Kind -->|Excel only| X["Parse workbook bytes"]
  Z --> Map["Column mapping + analysis UI"]
  X --> Map
  Map --> EI["ExcelImportService / ExhibitionImportService"]
  EI --> Dup{"ID match or fingerprint match?"}
  Dup -->|Yes| Update["Update existing record"]
  Dup -->|No| Create["Create new record"]
  EI --> MB["MediaBackupService — restore paths if ZIP"]
  Update --> Save["GemRecordService.saveRecord per row"]
  Create --> Save
```

### 6.8 Cloud backup ZIP

```mermaid
flowchart TD
  CB["CloudBackupService"] --> R["generateExcelBytes(records)"]
  CB --> M["Media files from record paths"]
  R --> Z["Create ZIP — excel + media"]
  M --> Z
  Z --> GD["GoogleDriveService upload — Android App Data"]
  Z --> Local["iOS / local path per platform"]
```

### 6.9 Analytics: currency rates on screen open

```mermaid
sequenceDiagram
  participant Ana as AnalyticsScreen
  participant CC as CurrencyConverterService
  participant API as Fawaz rates API
  participant SP as SharedPreferences
  Ana->>CC: refreshRatesIfNeeded()
  CC->>SP: read cache timestamp and rates
  alt cache stale and online
    CC->>API: GET rates JSON
    API-->>CC: USD currency map
    CC->>SP: persist rates and timestamp
  else cache fresh or offline
    CC-->>Ana: use cache or defaults
  end
```

### 6.10 Certificate image analysis (simplified)

```mermaid
flowchart TD
  F["File — certificate photo"] --> GVS["GemVisionService.analyzeCertificateImage"]
  GVS --> Q{"DeterministicExtractionServiceV2.aiExtractionEnabled?"}
  Q -->|false| DET["DeterministicExtractionServiceV2.extractCertificateData"]
  Q -->|true| OCR["Google Vision — raw text"]
  OCR --> ENT{"AppEntitlementsService.hasAI?"}
  ENT -->|yes| GPT["GPT structuring — ai_service path"]
  ENT -->|no| DET2["Fallback deterministic"]
  DET --> OUT["GemImageAnalysis"]
  GPT --> OUT
  DET2 --> OUT
  OUT --> Dlg["CertificateResultsDialog → merge into GemInputScreen"]
```

### 6.11 File intent while app running (optional path)

```mermaid
flowchart TD
  OS["OS opens file with app"] --> FH["FileHandlerService listener"]
  FH --> M["main.dart / routing logic"]
  M --> Imp["May navigate or pass path toward Import flow"]
```

---

## 7. Notable integrations

- **Google Sign-In / Drive:** Backup upload to App Data folder (Android); see `google_drive_service.dart`, `cloud_backup_service.dart`.
- **Currency rates:** HTTP fetch from Fawaz Ahmed CDN / fallback URL; 24h cache in `SharedPreferences` (`CurrencyConverterService`).
- **Certificate images:** File-based; optional Google Vision + GPT path behind flags/entitlements vs **deterministic** extraction (`DeterministicExtractionServiceV2`).

---

## 8. Theming

- `lib/theme/app_theme.dart` — Material 3, `surfaceTintColor: Colors.transparent` where set to avoid default M3 tint on bars.

---

## 9. Key packages (non-exhaustive)

See `pubspec.yaml` for versions: `hive_flutter`, `http`, `excel`, `archive`, `shared_preferences`, `image_picker`, `file_picker`, `share_plus`, `mobile_scanner` (QR), etc.

---

## 10. Build & release

- Standard Flutter: `flutter build apk` / `flutter build appbundle` / iOS equivalents.
- Signing and store listing are outside this doc.

---

## 11. Documentation set

| File | Role |
|------|------|
| [FUNCTIONAL.md](./FUNCTIONAL.md) | Product behavior and flows |
| This file | Architecture and code map |
| [AGENTS.md](../lib/theme/AGENTS.md) | AI agent rules + field checklist + constraints |

---

## 12. Changing system fields

Adding/removing/renaming a **core** `GemRecord` field touches many files. Follow the **checklist table** in `lib/theme/AGENTS.md` (*Core (system) field changes*).

---

*Update this file when architecture, dependencies, persistence, major service boundaries, or key control flows change (including §6 diagrams).*
