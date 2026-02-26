# v5 Improvements Analysis

Analysis of the plan-details panel spec (sections 1–13) against **plan-details-panel-v5.html**, with concrete improvements for v5 and additions to each field’s details section.

---

## 1. Current v5 vs spec (gap summary)

| Spec area | v5 today | Gap |
|-----------|----------|-----|
| **Author-first, single source of truth** | Goal card, summary line, version dropdown | No intent source, confidence, or “paraphrase”; no approval workflow |
| **Compact / Detailed** | ✅ Toggle exists | Detailed shows only Validation, Placeholder, Default per field |
| **Section cards** | Collapsible sections with step number, actions | No field count, completeness badge, complexity (Low/Med/High), section purpose, or mini-mockup |
| **Field chips** | Label, type icon, required *, PII/Confidential/Restricted/Fragment badges | No conditional badge, validation-format badge, hover preview of help/example |
| **Color-coded** | Required = red *; callouts (tip/info/success) | No gold for accessibility/consent; no orange/red for warnings/errors |
| **One-click actions** | Add field, Edit validation/options per section; AI icon on consent/thank you | No Edit/Duplicate/Remove/Move per field; no “Suggest improvements” per field |
| **Field “rich spec”** | 3 rows: Validation, Placeholder, Default | Missing: Role, Required rationale, Help text, Error messages, Conditional logic, Accessibility, Privacy details, Backend mapping, Analytics, i18n, QA checklist |
| **Section-level richness** | Section title + step number | No purpose, requiredness summary, bulk rules, compliance, test data button, change impact |
| **Global metadata** | Title, badge, metrics, summary, goal card, version | No last edited + author, intent source, confidence, suggested next actions, version history/diffs, approval |
| **Developer view** | JSON tab only | No Author/Developer toggle, no schema copy, no component/API mapping, ARIA snippets, CSS tokens |
| **Test & QA** | — | No sample submissions, simulated flow, edge-case simulator, a11y preview |
| **Export & collaboration** | — | No export (JSON/PDF/Excel), share link, acceptance-criteria export |
| **Narrative templates** | — | No consent/error copy library, template bank |
| **Suggestions with icons** | Category badges in optimization list (v5) | Can align badge set with spec (Pro tip, Helper, etc.) |

---

## 2. Improvements to v5 (prioritized)

### 2.1 Panel header & global metadata (spec §5)

- **Intent source**
  - Add a collapsible block: “Original prompt” + “Interpreted as” (paraphrase) so the plan is clearly the single source of truth.
- **Last edited**
  - Under title or summary: “Last edited by [Author] · [timestamp]”.
- **Confidence**
  - Optional confidence score (e.g. 0–100) per section or whole plan; tooltip with short “reasons” (e.g. “High: clear goal, known field types”).
- **Suggested next actions**
  - Keep “Proceed with plan” / “Modify plan”; optionally add “Export spec” and “Send for review”.
- **Version history**
  - Extend version dropdown: “Version 1 (current)” with a “View history” or “Compare versions” that shows a small timeline and diff summary (e.g. “2 fields added in Personal info”).

### 2.2 Section cards (spec §2, §4)

- **Section header**
  - Add to each section card header:
    - **Field count**: e.g. “6 fields”.
    - **Completeness badge**: e.g. “Complete” / “Draft” (could derive from required fields filled).
    - **Complexity**: “Low” | “Medium” | “High” (e.g. from field count + validations + conditionals).
  - Optional small **section icon** (e.g. person for Personal info, calendar for Subscription).
- **Section-level block (expandable or under header)**
  - **Section purpose**: One line, e.g. “Collect contact and identity for application processing.”
  - **Requiredness summary**: “2 required, 4 optional” for that section.
  - **Bulk rules** (if any): e.g. “Make all fields required” or “DOB not required in EU.”
  - **Compliance**: Short note (e.g. “Data residency: EU optional fields may vary.”).
  - **Test data**: Button “Generate test data” for that section (multi-locale).
  - **Change impact**: Short line, e.g. “Affects: email notification, CRM mapping.”

### 2.3 Field row (chips) and hover (spec §2)

- **Badges on the row (compact)**
  - **Conditional**: e.g. “If [X] = Yes” badge when the field is shown conditionally.
  - **Validation**: Small “Format” or “Regex” badge when a pattern is defined.
  - Keep: type icon, required *, PII/Confidential/Restricted/Fragment.
- **Color**
  - Required: keep red * (and optional red badge if desired).
  - Optional: neutral/grey badge.
  - Accessibility/consent: gold badge where relevant (e.g. consent, a11y-related fields).
  - Warnings: orange (e.g. “Consider making optional”); errors: red (e.g. “Missing label”).
- **Hover**
  - On field row hover: show a small tooltip or inline preview with **help text** and **example value** (from the field’s detail spec).

### 2.4 One-click actions (spec §2)

- **Per field**
  - Add small actions next to each field (icon row or dropdown):
    - **Edit** (pencil), **Duplicate**, **Remove**, **Move** (up/down or drag).
    - **Suggest improvements** (AI): opens or reveals a short list of suggested label/placeholder/validation changes.
- **Per section**
  - Keep “Add field”, “Edit validation/options”; ensure they feel consistent with field-level actions.

### 2.5 Mini-mockup (spec §2)

- **Section thumbnail**
  - Optional small “mockup” thumbnail per section (desktop/mobile toggle) showing a rough layout of that section’s fields.
  - Click: open a **quick mockup** (style/layout only, not full preview tab) in a modal or side panel.

### 2.6 Developer tab (spec §8)

- **Author / Developer toggle**
  - Tabs or toggle: “Author” (current Compact/Detailed/Preview/Structure/JSON) vs “Developer”.
- **Developer view**
  - **JSON schema**: Current JSON tab content + “Copy” button.
  - **Component mapping**: Table or list: Field → Component (e.g. `TextInputV2`), props, theme tokens.
  - **API mapping**: Endpoint + sample request payload.
  - **ARIA snippets**: Per field or per section, code snippet for ARIA attributes.
  - **CSS tokens**: Font, spacing, theme tokens used.

### 2.7 Export & collaboration (spec §10)

- **Export**
  - Buttons or menu: “Export JSON schema”, “Export PDF spec”, “Export Excel field map”, “OpenAPI mapping” (if applicable).
- **Share & review**
  - “Share for review”: link that opens a commentable view with anchored comments per field/section.
- **Acceptance criteria**
  - “Export acceptance criteria”: one-click generate tasks (e.g. Jira/Asana templates) prefilled from plan.

### 2.8 Narrative templates (spec §11)

- **In-panel library**
  - Section or tab: “Suggested copy” — consent samples (short, legal, plain), confirmation messages, common error messages.
  - **Template bank**: e.g. “Government ID intake”, “Subscription sign-up”, “Support request” with “Apply” or “Merge” to current plan.

---

## 3. Additions to the details section of each field (spec §3)

Current v5 **field-detail-block** (Detailed view) shows only:

- Validation  
- Placeholder  
- Default  

Below is the **full “rich spec”** to support per field (collapsed by default, expand for details). Group into logical subsections so authors can skim or go deep.

### 3.1 Core (always useful)

| Item | Description | Example / note |
|------|-------------|----------------|
| **Label (proposed)** | Current label text | “First name” |
| **Type** | text / email / date / dropdown / checkbox / phone / address / UCI / etc. | Already implied by icon; can show explicitly |
| **Role/Group** | Personal Info, Accessibility, Consent | For filtering and compliance |
| **Required** | Yes/No | Already shown with *; add **rationale** (e.g. “Legal”, “UX”, “Regulatory”) |
| **Help text** | Author-facing note + user-facing help | “Shown under the field; keep under 100 chars.” |
| **Placeholder / Example** | With locale when relevant | Already have Placeholder; add “Example value” and “Localized examples” |
| **Starting value / Default** | If any | Already as “Default” |

### 3.2 Validation (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Pattern or format** | Regex or named rule (e.g. numeric, UCI 9–10 digits) | `^\d{9,10}$` or “Numeric only, length 9–10” |
| **Min/max length, allowed chars** | Explicit limits | Min: 1, Max: 50; Letters and spaces |
| **Server-side validation** | Flag: “Server-side validation required” | Yes/No |
| **Error messages** | Exact copy per failure mode | Empty: “This field is required”; Pattern: “Your UCI should contain 9 or 10 digits.” |

### 3.3 Conditional logic (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Visual mini-rule** | Short sentence | “Show if [Do you have special needs?] == Yes” |
| **Rule builder** | Link or button | “Open rule builder” |

### 3.4 Accessibility (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **ARIA role** | role attribute | textbox, combobox, etc. |
| **Required announcement** | What screen readers should say | “Required” |
| **Label associations** | aria-labelledby / aria-describedby | aria-describedby="firstNameHelp" |
| **Focus behavior** | Tab order, focus management | — |
| **Recommended alt text** | For image/icon in field | — |
| **Screen reader summary** | One-line summary for a11y | “First name, required, letters and spaces.” |

### 3.5 Privacy & classification (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Sensitivity tag** | PII, Financial, Health, None | Already have PII/Confidential/Restricted |
| **Retention guideline** | How long to keep | “90 days”, “Until consent withdrawn” |
| **Encryption at rest** | Flag | Yes/No |

### 3.6 Backend & analytics (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Backend mapping** | Target field in API/DB, data type | applicant.firstName (string) |
| **Sample payload** | JSON snippet | `{ "firstName": "Jane" }` |
| **Analytics events** | Suggested events | field_focus, field_error, field_submit_success |

### 3.7 Internationalization (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Languages available** | List | en, fr, de |
| **Fallback** | Default locale | en |
| **Locale-specific rules** | e.g. DOB optional in some regions | “DOB optional in EU” |

### 3.8 QA checklist (expandable)

| Item | Description | Example |
|------|-------------|--------|
| **Quick checks** | Character limits, format | “Test max length 50” |
| **Negative tests** | What to try | “Submit empty”, “Invalid email” |
| **Edge cases** | Notes | “Leading zeros for UCI”, “Whitespace trim” |

### 3.9 Author guidance (inline / expandable) (spec §6)

| Item | Description | Example |
|------|-------------|--------|
| **Why this field?** | Short rationale (expand) | “Required for identity verification.” |
| **Microcopy variants** | Formal vs plain + tone | “Formal: ‘Given name’; Plain: ‘First name’” |
| **Best practice hint** | e.g. “Avoid DOB unless necessary” | With alternative: “Consider age confirmation checkbox.” |
| **Privacy-first suggestion** | e.g. “Consider postal code only” | “Consider not collecting full address.” |

---

## 4. Suggested UI for field details in v5

- **Compact**: Keep current row (label, type icon, required *, badges). Optionally add conditional + validation badges and hover preview (help + example).
- **Detailed**: Keep the existing **field-detail-block** as the “first fold” with:
  - Label, Type, Role/Group, Required + rationale, Help text, Placeholder, Example, Default.
  - Then **expandable subsections** (e.g. accordions or “Show more”):
    - **Validation** (pattern, min/max, server-side, error messages)
    - **Conditional logic** (mini-rule + link to rule builder)
    - **Accessibility** (ARIA, label, focus, screen reader summary)
    - **Privacy & classification** (sensitivity, retention, encryption)
    - **Backend & analytics** (mapping, sample payload, events)
    - **Internationalization** (languages, fallback, locale rules)
    - **QA checklist** (quick checks, negative tests, edge cases)
    - **Author guidance** (Why this field?, microcopy, best practice, privacy suggestion)

- **Per-field actions** in the row: Edit, Duplicate, Remove, Move, Suggest improvements (AI).

This keeps the panel author-first, supports both skim (compact + first fold) and deep dive (expandable blocks), and aligns with the spec’s “rich spec” and phased rollout (e.g. Phase 2 field expansion, Phase 3 a11y/privacy, Phase 4 collaboration).

---

## 5. Phased implementation (from spec §12)

- **Phase 1 (already in v5 or small add)**  
  Compact/Detailed, section cards with step numbers, goal + summary, version, JSON.  
  Add: section field count + optional complexity badge; intent source (prompt + paraphrase).

- **Phase 2**  
  Field detail expansion: help text, placeholder, example, required + rationale; per-field Edit/Duplicate/Remove/Move; basic validation recommendations and “Apply rule”; version history.

- **Phase 3**  
  Accessibility and privacy auto-audits with quick-fixes; Developer tab (API mapping, ARIA snippet); test data generator and simulated run.

- **Phase 4**  
  Collaboration (comments, approvals); advanced AI (microcopy, data minimization); analytics/telemetry suggestions.

---

## 6. Example: UCI and Special needs (spec §13) in v5 terms

**Compact line:**

- **UCI (Unique Client Identifier)** · Text · Required · PII  
  [Optional: Validation badge “Format”]

**Detailed (expandable):**

- **Label:** UCI (Unique Client Identifier)  
- **Type:** Text · **Required** · **Rationale:** Regulatory  
- **Example:** 123456789  
- **Validation:** Numeric only, length 9–10. Suggested regex: `^\d{9,10}$`  
- **Error messages:** Empty: “This field is required”; Pattern: “Your Unique Client Identifier should contain 9 or 10 digits.”  
- **Backend:** applicant.uci (string)  
- **Accessibility:** aria-describedby="uciHelp"  
- **QA:** Test with leading zeros, whitespace trimming  

**Special needs (conditional):**

- **Do you have special needs requiring accommodation?** · Radio · Required  
- **Options:** Yes / No (suggested: use Yes/No instead of Agree/Disagree)  
- **If Yes** → Show “Type of accommodation required” (Dropdown)  
- **If Other** → Show “More information” (large text, max 1000)  
- **Suggested microcopy:** “If you need assistance such as wheelchair access, sign language interpretation, or documents in large print, let us know.”  
- **Privacy:** No PII by default; free text may contain PII — mark for review.

Implementing these in v5 would mean adding conditional badges and an expandable “Conditional logic” + “Suggested microcopy” block in the field details, plus the extra validation/error/backend/QA rows above.

---

*End of analysis. Use this document to prioritize v6 (or incremental v5) changes and to define the exact field-detail schema and copy for authoring/export.*

---

## v7 scope (implemented)

**plan-details-panel-v7.html** implements the following from this analysis:

- **2.1** Panel header: intent source (collapsible), last edited, confidence score, Export spec / Send for review
- **2.2** Section cards: field count, completeness badge, complexity; section purpose, requiredness, compliance, change impact, Generate test data button
- **2.3** Field row: conditional/format badges, hover tooltip (data-help), color-coded badges (gold/orange/red)
- **2.4** Per-field actions: Edit, Duplicate, Remove, Move, Suggest improvements (reveals mock suggestions)
- **2.5** Field detail expansion: Role, Required rationale, Example; expandable Validation details, Accessibility, Backend (First name and Email fully populated)
- **2.7** Developer tab: Author/Developer toggle; JSON schema + Copy; component mapping table; API mapping; ARIA snippet
- **2.8** Export: Export JSON, Export PDF, Share for review, Export acceptance criteria (buttons in panel)
- **2.9** Narrative templates: Suggested copy (consent, confirmation, error) with Use; Template bank (Government ID, Subscription sign-up, Support request)
