# BUILD TASK: Rebuild 934th CES Promotion Eligibility Worksheet

## Overview
Completely rebuild `index.html` — the 934th Civil Engineering Squadron Promotion Eligibility Worksheet. This is a single self-contained HTML file (no external dependencies) used by Air Force Reserve supervisors to score enlisted members for promotion eligibility.

## What Exists
- `index.html` — Current version (functional but needs major UI/UX overhaul)
- `research-af-reserve-promotion.md` — AF Reserve promotion requirements research
- `research-ce-requirements.md` — CE career field training requirements by AFSC
- `local-policy.md` — 934th CES local scoring policy (the actual worksheet criteria)
- `../research/3E7X1_promotion_requirements.json` — Detailed Fire Protection certification matrix
- `../research/ce-afsc-requirements.md` — CE AFSC Group 1 requirements (Electrical, Power Pro, HVAC, Pavements, Structural)
- `../research/ce-afsc-requirements-group2.json` — CE AFSC Group 2 requirements (Water/Fuel, Pest Mgmt, Engineering, EOD, EM)
- `../research/scoring-worksheet-ux-recommendations.md` — UX design recommendations

## CRITICAL: Read ALL research files before building
Read every file listed above. The research files contain the exact certification requirements that must be embedded in the tool.

## Requirements

### 1. Core Scoring Worksheet (Keep from existing)
The scoring criteria from `local-policy.md` must be preserved exactly:
- **Integrity First** (8 items, 0-3 scale each, max 24)
- **Service Before Self** (8 items, 0-2 scale each, max 16)
- **Excellence In All We Do** (8 items, mostly 0-1 scale, max 9)
- **Bonus Points** (3 items, max 6)
- **Behavioral Assessment** (3 Y/N items, not scored)
- **Grand Total: 48 points max**
- **Promotion Thresholds**: TSgt min 26/PEP 32, MSgt min 32/PEP 38, SMSgt min 38/PEP 44

### 2. NEW: AFSC-Specific Requirements Auto-Population
When a user selects their **Current Rank** and **AFSC**, a new section should appear showing all requirements for promotion to the NEXT grade. Each requirement should be a checkbox item that the user can check off.

Requirements must be organized by category:
- **Certifications** (IFSAC/ProBoard, EPA, DoD, etc.)
- **Training** (skill level upgrade, OJT, craftsman course, CDCs)
- **PME** (ALS, NCOA, SNCOA)
- **Administrative** (TIG/TIS, CCAF degree, medical, etc.)

#### AFSCs to support (all 934th CES career fields):
1. **3E0X1** — Electrical Systems
2. **3E0X2** — Electrical Power Production
3. **3E1X1** — HVAC/R
4. **3E2X1** — Pavements & Construction Equipment
5. **3E3X1** — Structural
6. **3E4X1** — Water & Fuel Systems
7. **3E4X3** — Pest Management
8. **3E5X1** — Engineering
9. **3E7X1** — Fire Protection (MOST DETAILED — use the JSON research file)
10. **3E8X1** — Explosive Ordnance Disposal
11. **3E9X1** — Emergency Management

#### Grade transitions to support:
- SrA (E-4) → SSgt (E-5)
- SSgt (E-5) → TSgt (E-6)
- TSgt (E-6) → MSgt (E-7)
- MSgt (E-7) → SMSgt (E-8)

#### Data source mapping:
- **3E7X1**: Use `../research/3E7X1_promotion_requirements.json` — this has the most detailed data with full certification progression matrix
- **3E0X1, 3E0X2, 3E1X1, 3E2X1, 3E3X1**: Use `../research/ce-afsc-requirements.md`
- **3E4X1, 3E4X3, 3E5X1, 3E8X1, 3E9X1**: Use `../research/ce-afsc-requirements-group2.json`

### 3. UI/UX Design Requirements

Read `../research/scoring-worksheet-ux-recommendations.md` for full design details. Key points:

#### Layout
- **Single page with accordion sections** + sticky navigation
- Desktop: sidebar nav showing sections + subtotals
- Mobile: sticky top nav + floating bottom score bar
- All sections start expanded on load

#### Scoring Controls
- **Segmented button controls** (NOT dropdowns) for scoring
- Single tap to select score value
- Color-coded by score: red(0) → orange(1) → teal(2) → green(3)
- 44px minimum tap targets for mobile
- Use hidden radio inputs with styled labels (accessible)

#### Progress & Totals
- Section headers show subtotals + mini progress bars + completion counts
- 3px global progress bar at top
- All update live on every score change
- Mobile: fixed bottom bar with grand total

#### Smart Features
- **LocalStorage auto-save** — critical for drill weekend use (survives page reload)
- Auto-populate AFSC requirements section when rank + AFSC selected
- Conditional section visibility based on selections
- Auto-filled items marked with blue left border + "Auto-filled" label

#### Colors & Theming
- USWDS-inspired navy/teal palette
- Dark mode via `prefers-color-scheme` + manual toggle
- Score colors all WCAG AA compliant
- CSS custom properties for all colors

#### Print
- Complete `@media print` stylesheet
- Formal document format (Times New Roman, table layout)
- Signature lines for Ratee and Rater
- Score summary table
- Hidden interactive elements
- Force all accordions open
- Show selected scores as text values

#### Typography & Tech
- `system-ui` font stack (no external fonts)
- Pure vanilla JS — no frameworks, no external dependencies
- CSS Grid + Flexbox for layout
- `prefers-reduced-motion` respected
- Single self-contained HTML file

### 4. Member Information Section
- Member Name (text input)
- Current Rank (select — E-1 through E-8)
- AFSC (select — all 11 CE AFSCs listed above)
- Supervisor Name (text input)
- Date (auto-fills today)
- **Promoting To** (auto-calculated based on current rank selection)

### 5. Additional Features
- **Reset All** button with confirmation
- **Print / Save PDF** button
- **Clear Saved Data** option (clears LocalStorage)
- **Expand All / Collapse All** toggle
- Commander's Note at bottom: "Good Attitude, Performance and Participation are not occasional, convenient, or one time occurrences — they are continuous characteristics."
- Note about members in overtime training not being eligible

## Technical Constraints
- **Single HTML file** — everything inline (CSS + JS)
- **No external dependencies** — no CDN, no frameworks
- **Target size: 50-80KB** — acceptable for a data-rich tool
- **Must work offline** — no network requests
- **Browser support: modern browsers** (Chrome, Safari, Firefox, Edge)

## File to create/overwrite
Output: `index.html` (overwrite the existing file)

## Quality Bar
- Mobile-first responsive design
- All interactive elements accessible via keyboard
- ARIA labels on all form controls
- Print output looks like a formal military document
- Score calculations are correct (verify against local-policy.md thresholds)
- Every AFSC has at least basic requirements populated for each grade transition
- Fire Protection (3E7X1) has the most detailed requirements (it's the unit commander's AFSC)
