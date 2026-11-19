# AHA/ACC Acute Pulmonary Embolism (PE) Clinical Categories Selector

An interactive, visual matrix widget implementing the **AHA/ACC Acute Pulmonary Embolism Clinical Categories** (Categories **A** through **E**, subcategories **B1–E2**, and respiratory failure **`+R`** modifiers).

Based on the AHA/ACC clinical guidelines ([Circulation DOI: 10.1161/CIR.0000000000001415](https://www.ahajournals.org/doi/10.1161/CIR.0000000000001415)) and the accompanying [AHA/ACC Acute PE Clinical Categories Infographic](https://professional.heart.org/-/media/PHD-Files-2/Science-News/a/AHA-ACC-Acute-PE-Clinical-Categories-Figure-Inforgraphic.pdf).

## Features

- **Visual Card Matrix:** Accessible, responsive image-based radio controls laid out to mirror the official AHA/ACC clinical category grid.
- **Column-Locked Modifiers (`+R`):** Respiratory failure modifiers (`C+R`, `D+R`, `E+R`) are dynamically enabled only when a core category or subcategory in the matching column (`C`, `D`, or `E`) is selected.
- **Auto-Reset & Toggle Behavior:**
  - Switching core selections to a different column automatically unchecks and disables any previously active `+R` modifier.
  - Clicking or pressing `Space`/`Enter` on an already-selected `+R` modifier unselects it.
- **Parent Form & Data Syncing:** Automatically maps the user's visual selection into 6 structured fields and syncs them to a parent form (same-page or via `<iframe>` / `postMessage`):
  - `iaat_acu_pul_emb_cli_cat` — Major category (`A`–`E`)
  - `iaat_acu_pul_emb_cli_cat_b` — Subcategory (`B1`, `B2`)
  - `iaat_acu_pul_emb_cli_cat_c` — Subcategory (`C1`, `C2`, `C3`)
  - `iaat_acu_pul_emb_cli_cat_d` — Subcategory (`D1`, `D2`)
  - `iaat_acu_pul_emb_cli_cat_e` — Subcategory (`E1`, `E2`)
  - `iaat_acu_pul_emb_cli_cat_r` — Modifier (`C+R`, `D+R`, `E+R`)

## Repository Structure

```text
├── index.html              # Main interactive matrix widget (HTML/CSS/jQuery)
├── README.md               # Project documentation
└── images/                 # Category cards and modifier graphics
    ├── aha_a.png
    ├── aha_b.png, aha_b1.png, aha_b2.png
    ├── aha_c.png, aha_c1.png, aha_c2.png, aha_c3.png, aha_c+r.png
    ├── aha_d.png, aha_d1.png, aha_d2.png, aha_d+r.png
    ├── aha_e.png, aha_e1.png, aha_e2.png, aha_e+r.png
    └── plusminus.png
```

## Usage

1. Ensure the `images/` directory resides in the same folder as the HTML file.
2. Open the HTML file directly in any modern browser or embed it inside an `<iframe>` within a parent data-capture form (e.g., REDCap, Qualtrics, or a custom web form) containing matching input names (`iaat_acu_pul_emb_cli_cat*`).
3. Current selection state is exposed globally via `window.ahaSelection` and logged to the browser console on every change.

## Dependencies

- [jQuery 3.7.1](https://jquery.com/) (loaded via Google Hosted Libraries CDN)
