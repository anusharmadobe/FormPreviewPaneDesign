# Form Preview Pane Design

Design prototypes for the **Plan Details Panel** (right-hand panel) in an AEM/Adobe form creation flow. The panel lets users review and refine a generated form plan before building it—structure, fields, context, optimization suggestions, and a live-style preview.

### Quick start

```bash
git clone https://github.com/anusharmadobe/FormPreviewPaneDesign.git
cd FormPreviewPaneDesign
open PreviewForm/cursor-agent/plan-details-panel-v12.html
```

Then use the **Compact** | **Detailed** | **Preview** | **JSON** buttons in the right panel to switch views.

---

## What this is

- **Static HTML prototypes** of the improved “Plan Details” right panel.
- **No build step or server**—open any `.html` file in a browser to use it.
- **Single-file demos**—each version is one HTML file with embedded CSS and JavaScript.
- The sample plan is a **subscription sign-up form** (personal details, subscription preferences, consent, submit) used to demonstrate layout, sections, views, and behavior.

The panel appears in a **three-column layout**:

| Area | Role |
|------|------|
| **Left** | Narrow sidebar (e.g. nav/icons). |
| **Center** | Main content—e.g. “Plan created” card with **Modify the plan** / **Proceed with the plan as is**. |
| **Right (1/3)** | **Plan Details Panel**—title, metrics, view toggle (Compact / Detailed / Preview / JSON), sections, context, optimization, and (in some versions) next steps. |

---

## How to view

1. Clone the repo (or download the files).
2. Open the prototype in a browser:

   ```bash
   open PreviewForm/cursor-agent/plan-details-panel-v12.html
   ```

   Or double-click the file in Finder, or drag it into a browser window.

3. Use the **view toggle** in the right panel to switch between **Compact**, **Detailed**, **Preview**, and **JSON**.

No local server or install is required.

---

## Screenshots / What to expect

| View | What you’ll see |
|------|------------------|
| **Compact** | Right panel: section list (1 Branding…, 2 Personal information 5 fields, 3 Subscription details 3 fields, 4 Consent & submit). Each section expands to show field names only. No context block. |
| **Detailed** | Same panel with **Context** at top (Goal, Audience, Intent). Then the four sections; each has an optional Purpose block and a field list. Each field can show Role, Validation, Placeholder, Default, expandable Validation / Accessibility / Backend, and action buttons (Edit, Duplicate, Remove, Suggest). **Optimization opportunities** list at the bottom with **Apply** and **Apply all**. |
| **Preview** | Right panel shows only the form: “Personal information” and “Subscription details” with inputs, consent checkbox, and a **Subscribe** button—no plan UI. |
| **JSON** | Right panel shows pretty-printed JSON: `title`, `theme`, `description`, `sections[]`, `consent`, `submitButton`, `thankYouMessage`, `submission`. |

*(Screenshots can be added here later—e.g. `docs/compact.png`, `docs/detailed.png`, `docs/preview.png`, `docs/json.png`.)*

---

## View modes (Compact, Detailed, Preview, JSON)

The right panel has four modes, selected by the buttons under the metrics:

| View | What it shows |
|------|-------------------------------|
| **Compact** | Section list only: section names and field names. **Context** is hidden. Collapsible section headers (chevron right when collapsed, down when expanded). Good for a quick scan of structure. |
| **Detailed** | Full plan: **Context** (Goal → Audience → Intent), all sections with **Purpose** (except Branding, where Purpose is hidden), and every field with full details: role, validation, placeholder, default, required rationale, expandable blocks for Validation details, Accessibility, Backend. Per-field actions (Edit, Duplicate, Remove, Suggest). Optimization section is expanded by default. |
| **Preview** | Rendered form as an end user would see it: sections (Personal information, Subscription details), labels, inputs, consent checkbox, and **Subscribe** button. No plan UI—just the form. |
| **JSON** | Form structure as JSON: `title`, `theme`, `description`, `sections` (with `fields`), `consent`, `submitButton`, `thankYouMessage`, `submission`. Useful for integration or export. |

- **Compact**: minimal context; sections and fields only; expand/collapse sections.
- **Detailed**: full context (Goal, Audience, Intent), Purpose blocks (except Branding), and full field metadata and actions.
- **Preview**: live-style form only.
- **JSON**: raw structure.

---

## How it works (structure and behavior)

### Panel header (all views)

- **Title**: e.g. “Subscription sign-up form with personal details”.
- **Subtitle**: e.g. “Review structure, fields, and options before you build.”
- **Version** dropdown (e.g. Version 1/2/3).
- **Badge**: e.g. “Plan – Ready to begin”.
- **Metrics**: e.g. “~3 min” (est. filling time), “~24%” (est. conversion rate).
- **View toggle**: Compact | Detailed | Preview | JSON.

### Context (Compact vs Detailed)

- **Compact**: No context block (removed for minimal view).
- **Detailed**: A **Context** card with:
  - **Goal** – one paragraph.
  - **Audience** – one paragraph.
  - **Intent** – “Original prompt” and “Interpreted as” rows.

### Sections (form plan)

1. **Branding, Layout and Style** – Theme and template (e.g. Lively theme, Frescopa template), “8 fields · 3 sections.” Purpose block is **hidden** in Detailed view.
2. **Personal information** – 5 fields (Full name*, DOB, Email*, Phone, Address). Purpose, requiredness, compliance, change impact. In Detailed view: per-field Role, Validation, Placeholder, Default, Required rationale, Validation details, Accessibility, Backend.
3. **Subscription details** – 3 fields (Start date*, Preferred coffee type*, Delivery frequency). Same idea: Purpose and, in Detailed view, full field metadata.
4. **Consent & submit** – Consent checkbox, Submit button label (e.g. “Subscribe”), thank-you message, where to send data, post-submit options.

Sections are **collapsible** (click header). Chevron points **right** when collapsed, **down** when expanded.

### Optimization opportunities

- Collapsible block (in Detailed view it starts expanded).
- Suggestions with category (Pro tip, Helper, Layout & structure, Translation, Simplification, etc.), short text, and an **Apply** button (grey, same style as “Apply all”).
- **Apply all** button in the header of the block.

### Sample form (Preview)

- **Personal information**: Full name*, Date of birth, Email*, Phone, Address.
- **Subscription details**: Start date*, Preferred coffee type*, Delivery frequency (Daily/Weekly/Bi-weekly/Monthly).
- Consent checkbox*, **Subscribe** button.

---

## File layout and versions

| Path | Description |
|------|-------------|
| **PreviewForm/cursor-agent/plan-details-panel-v12.html** | **Current prototype** – Compact/Detailed (with context and no-context), Preview, JSON; Branding without Purpose in Detailed; grey Apply buttons; Layout & Structure merged; Subscribe in preview and JSON. |
| PreviewForm/cursor-agent/plan-details-panel-v11.html | Earlier iteration (e.g. before context reorder, section count 3). |
| PreviewForm/cursor-agent/plan-details-panel-v10.html … plan-details-panel.html | Older versions (different features per v). |
| PreviewForm/cursor-agent/README.md | Short folder-level notes and version list. |
| PreviewForm/claude-code/ | Other prototype variants (e.g. hybrid, maximum-impact). |

**Recommended file to open:** `PreviewForm/cursor-agent/plan-details-panel-v12.html`.

---

## Tech notes

- **HTML + CSS + JS** in one file; no framework.
- **Font**: Inter (Google Fonts).
- **Colors**: AEM purple (`#6e0ff5`), neutrals, semantic (required red, success green, etc.).
- **Behavior**: View switching, section/purpose/optimization expand-collapse, field expand blocks in Detailed view; JSON is generated from an in-page JavaScript object.

---

## Repo

- **URL**: https://github.com/anusharmadobe/FormPreviewPaneDesign.git  
- **Branch**: `main`.
