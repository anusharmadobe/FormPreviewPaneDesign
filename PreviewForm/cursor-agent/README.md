# Plan Details Panel – Prototype

This folder contains a **static HTML prototype** of the improved right-panel (Plan Details) for the form creation flow.

## What’s in the prototype

- **Summary line:** e.g. “12 fields · 2 sections · Canvas theme · ~5 min”
- **Goal** in a highlighted block
- **Primary actions** in the panel (Proceed / Modify)
- **Grouped sections:** Form setup, Personal information, Subscription details, Legal & submit
- **Expand/collapse** section headers (click to toggle)
- **Step checkboxes** – check off steps; progress bar updates
- **Field-level details** – type (Text, Email, Date, etc.) and Required/Optional
- **Short tips** where relevant (e.g. Date of birth optional per region)
- **“Edit step”** links per step
- **Progress:** “X of 5 steps completed” and a progress bar
- **“Save as form template”** link

## How to view

Open in a browser:

```bash
open PreviewForm/cursor-agent/plan-details-panel.html
```

Or double-click `plan-details-panel.html` in Finder, or drag it into a browser window.

## Files

- `plan-details-panel.html` – earlier prototype (no server required)
- `plan-details-panel-v2.html` – **v2**: versioning top-right, Goal+Audience merged (grey), Apply all next to “Optimization opportunities”, no Edit step, smart optional-field message, submission tiles with recommendation, thank you suggested by default
- `plan-details-panel-v3.html` – **v3**: no "backend integration"; * next to field label; no PII on Address and below + fragment tip; "Address line" → "Address"; version icon-only; consent (required *); no Submit step; thank you larger font, Suggested smaller/not bold, AI icon to edit
- `plan-details-panel-v4.html` – **v4 (Maximum Impact)**: 4-tile metrics (Est. time, Conversion, Total fields, Sections) in 2×2 grid; **Structure** tab with expandable tree of sections and field names; quick action per section (Add field, Edit validation, etc.); **AI-powered suggestions** block above Optimization
- `plan-details-panel-v5.html` – **v5 (Hybrid + Enhanced)**: builds on v4. **Preview** tab with rendered form as end users see it; Goal+Audience in a **card** (bordered, label "Goal"); **color-coded callouts** (tip=amber, info=blue, success=green); **step numbers** (1–4) on section headers
- `plan-details-panel-v6.html` – **v6**: builds on v5. **Category icons** (Pro tip, Helper, Structure, Translation, Consider, Layout) in Suggestions & optimization section
- `plan-details-panel-v7.html` – **v7**: builds on v6. **Full spec**: intent source, last edited, confidence; section purpose/complexity/test data; field chips (conditional, format badges), hover help, per-field actions (Edit/Duplicate/Remove/Move/Suggest); expanded field details (Role, Validation, Accessibility, Backend); Author/Developer toggle; Export (JSON/PDF/Share); narrative templates (suggested copy, template bank)
