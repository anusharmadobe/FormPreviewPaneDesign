# Form Preview Pane Design

Static HTML prototypes for the **Plan Details Panel** (right-hand panel) in a form-creation flow. Review a generated form plan—sections, fields, context, and preview—before building.

### Quick start

```bash
git clone https://github.com/anusharmadobe/FormPreviewPaneDesign.git
cd FormPreviewPaneDesign
open PreviewForm/cursor-agent/plan-details-panel-v12.html
```

Use the **Compact** | **Detailed** | **Preview** | **JSON** buttons in the right panel to switch views. No server or build step.

---

## What this is

- Single-file HTML prototypes (no dependencies). Open in a browser.
- Sample plan: a **subscription sign-up form** (personal info, subscription details, consent, submit).
- Layout: left sidebar, center (“Plan created” + actions), right panel = Plan Details (title, metrics, view toggle, sections, optimization).

---

## View modes

| View | What it shows |
|------|----------------|
| **Compact** | Section and field names only; no context. Collapsible sections. |
| **Detailed** | Full context (Goal, Audience, Intent), section Purpose, and per-field details (validation, accessibility, backend). Optimization suggestions with Apply. |
| **Preview** | Rendered form as users see it (inputs, consent, Subscribe button). |
| **JSON** | Form structure as JSON (sections, fields, consent, submitButton, thankYouMessage). |

---

## Files

- **PreviewForm/cursor-agent/plan-details-panel-v12.html** — current prototype (use this one).
- Older versions (v11, v10, …) and other variants live in `PreviewForm/cursor-agent/` and `PreviewForm/claude-code/`.

Repo: **https://github.com/anusharmadobe/FormPreviewPaneDesign.git**
