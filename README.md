# Transfection Master Mix & PowerPoint Calculator

**Live App (GitHub Pages):** https://zhuojin05.github.io/transfection-mastermix-calculator/

A zero-dependency, single-file browser workbench (`index.html`) for quantitative plasmid transfection master mix design, minimal-waste serial dilution planning, multi-format plate mapping, and native Microsoft PowerPoint table export.

Built for wet-lab researchers: runs completely offline via `file://` in any modern browser or via [GitHub Pages](https://zhuojin05.github.io/transfection-mastermix-calculator/)—no build step, server, or external CDN required.

---

## Key Features

### 1. Flexible Experimental Conditions & Plate Formats
- **Multi-format plate support:** `6-well (2×3)`, `12-well (3×4)`, `24-well (4×6)`, `48-well (6×8)`, and `96-well (8×12)` plates with one-click **↺ Apply Format Defaults**.
- **31 grouped transfection reagents (editable combobox):** Browse grouped presets across Lipofectamine, FuGENE/Promega, X-tremeGENE, Mirus TransIT, Polyplus (`jetPRIME`/`jetOPTIMUS`/`jetPEI`), and classic polymer reagents (`PEI MAX`, `PEI 25 kDa`, `PolyJet`, `TurboFect`, etc.)—or type any custom reagent freely. Also includes autocomplete datalists for complexation buffers (`Opti-MEM`, `HBS`, `Serum-Free DMEM`, etc.) and culture media (`DMEM`, `RPMI-1640`, `Neurobasal`, etc.).
- **Transfer volume mode:** Toggle between **Fixed** µL/well transfer or **Auto** exact volumetric transfer (`Tube Vol / Mix Scale`).

### 2. Quantitative Stoichiometry Modes
Each tube row supports five real-time calculation modes:
1. **Mock (Filler Only):** 100% empty-vector filler to match total DNA mass per tube.
2. **Single + Filler:** Fixed per-well DNA mass (`ng/well`) or **Match 1:1** molar dose equivalence to a paired co-expression control, automatically topped up with filler DNA.
3. **Fixed Total Molar (`A:B`):** Splits total DNA proportionally by construct length (`bp`) so exact molar stoichiometry $r_A : r_B$ is maintained:
   $$m_A = M_{\text{total}} \cdot \frac{r_A L_A}{r_A L_A + r_B L_B}, \qquad m_B = M_{\text{total}} - m_A$$
4. **Anchor Titration + Filler:** Holds Plasmid A constant at a fixed mass while titrating Plasmid B across molar ratios (`1:1`, `3:1`, `5:1`, `10:1`, `20:1`, `40:1`, or custom), filling the remainder with empty vector.
5. **Direct Mass Entry:** Manual per-well or per-tube `ng` entry with optional automatic filler balancing.

### 3. Minimal-Waste Multi-Tier Working Dilution Solver & Buffer Compensation
- When any raw plasmid pipetting volume drops below `Min Pipette (V_min)`, the shared solver automatically selects the **fewest pipettable working dilutions** per plasmid across single-step (`1:5`–`1:100`) and 2-step serial (`1:200`–`1:10000`, capped at ≤100× per step) tiers.
- Automatically chains compatible tiers (e.g., drawing from a `1:10` working tube to prepare `1:200`) and includes configurable dead-volume prep excess (`Prep Dead-Vol Excess %`).
- **Buffer Compensation:** Automatically subtracts extra aqueous volume introduced by diluted plasmid stocks from the complexation buffer so total mix volume stays constant across all tubes.

### 4. Interactive Plate Map, PowerPoint Export & `.pptx` Well-Map Import
- **Custom tube & well colors:** Pick any color for a tube/condition directly from either the Master Mix Reaction Builder or the Interactive Plate Map brush bar to repaint assigned wells and `.pptx` legends live.
- **Copy for PowerPoint (`Cmd+V` / `Ctrl+V`):** Copies rich inline-CSS HTML tables across **8 colorways** (*Classic Slate*, *Midnight Navy*, *Slate Blue*, *Royal Lavender*, *Soft Wisteria*, *Dusty Rose*, *Sakura Blush*, and *Monochrome*) with optional 2-line stacked cells and superscript dilution marks (`†`/`‡`/`§`) that paste directly as native editable PowerPoint tables.
- **Standalone `.pptx` Generator:** Pure-JS OOXML generator exports a 2-slide 16:9 presentation containing the formatted master mix table, dynamic `6–96` well plate map, condition legend, and working dilution prep recipes.
- **Offline `.pptx` Well-Map Importer:** Drag & drop any `6–96` well plate map `.pptx` onto the page to extract plate layout, construct legend (`bp` sizes), metadata, and transfection conditions.
- **Plate CSV (`_wellmap.txt`) & JSON Persistence:** Exports a 22-column well-level CSV log (`well`, `plasmid_1`, `mass_ng_1`, `plasmid_2`, `mass_ng_2`, `filler_ng`, etc.) and auto-saves workspace state to browser `localStorage` plus JSON import/export.

---

## Quick Start

1. Open the hosted tool directly at **https://zhuojin05.github.io/transfection-mastermix-calculator/** — or download/clone this repository and double-click [`index.html`](index.html) offline.
2. Choose **⚡ Demo** from the top menu to explore co-expression or titration examples, click **➕ Add Tube Row** to build a plan from scratch, or drag & drop an existing well-map `.pptx` anywhere on the page.

---

## License

Released under the [MIT License](LICENSE).
