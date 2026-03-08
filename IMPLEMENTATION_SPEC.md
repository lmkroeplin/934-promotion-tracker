# IMPLEMENTATION SPEC — Final Production Build

Read this entire file, then read `index.html`, then implement ALL changes described below. Overwrite `index.html` with the production-ready version.

## CRITICAL BUG FIXES (Must Fix)

### Fix 1: AFSC Requirements Never Display
In `updateAfscRequirements()`, change:
```js
section.style.display = '';
```
To:
```js
section.style.display = 'block';
```
The CSS rule `#afscRequirements{display:none}` overrides `style.display = ''` because removing the inline style just lets the stylesheet rule take effect.

### Fix 2: Print Stylesheet Hides AFSC Requirements
In the `@media print` CSS, remove `#afscRequirements` from the `display:none!important` list. AFSC requirements should print — they're the most important checklist.

### Fix 3: Remove Dead Variable
In `updateAll()`, delete: `var e = document.getElementById;`

### Fix 4: E-4 Threshold Message
Change `'Local worksheet thresholds apply E-5 (TSgt) and above.'` to `'Thresholds apply to SSgt (E-5) promotions and above. This scoring worksheet is designed for SSgt–MSgt selections.'`

## ACCESSIBILITY FIXES (Must Fix)

### A1: Add legends to all radio groups
Update `buildScoreControl()` to accept a `legendText` parameter and add a visually-hidden `<legend>`:
```js
function buildScoreControl(name, max, values, legendText) {
  // ... existing setup ...
  html += '<legend class="sr-only">' + (legendText || name) + '</legend>';
  // ... rest of function ...
}
```
Pass `item.text` as legendText from `buildSection()`, `buildBonusSection()`, and behavioral items.

### A2: Add aria-live to score displays
Add `aria-live="polite"` to: `#integrityScore`, `#serviceScore`, `#excellenceScore`, `#bonusScore`, `#thresholdBody`, and the mobile score bar.

### A3: Fix accordion focus management
Add the `inert` attribute to collapsed section content so keyboard users don't tab into hidden items:
```js
function toggleSection(btn) {
  var expanded = btn.getAttribute('aria-expanded') === 'true';
  btn.setAttribute('aria-expanded', !expanded);
  var content = btn.nextElementSibling;
  if (content) content.inert = expanded;
}
```
Also on page load, set `inert` on any section that starts collapsed.

### A4: Fix color contrast
Change score colors to pass WCAG AA (4.5:1):
```css
:root {
  --score-1: #9a4400; /* was #c05600 — now ~5.2:1 on white */
  --score-2: #0a6580; /* was #0d7ea2 — now ~5.0:1 on white */
}
```

### A5: Add aria-labels to score radio labels
Each label should have `aria-label="Score X of Y"`:
```js
html += '<label for="' + name + '-' + v + '" aria-label="Score ' + v + ' of ' + max + '">' + v + '</label>';
```

## UI/UX IMPROVEMENTS (Must Implement)

### U1: Header Redesign
Replace the flat header with a gradient military-style header:
- Background: `linear-gradient(135deg, #0a2647 0%, #1a4480 60%, #1e3a5f 100%)`
- Gold bottom border: `border-bottom: 3px solid #c5a44e`
- Add emblem space (use ★ star character as placeholder, or the 934th AW image)
- Subtitle "AIR FORCE RESERVE COMMAND" above the unit name
- "Promotion Eligibility Worksheet" below
- Box shadow for depth

### U2: Squadron Logo
Add the 934th Airlift Wing emblem in the header. Use this URL:
`https://upload.wikimedia.org/wikipedia/commons/d/d5/934th_Airlift_Wing.png`
Display as a 48-52px circle with gold border in the header. Add `loading="eager"` and include a text fallback (★) if the image fails to load.

### U3: Section Headers — Left Border Accent
Change section headers from full-width blue background to:
- White/surface background with left border accent: `border-left: 4px solid var(--primary)`
- Section icons (emoji) before each title:
  - Member Info: 📋
  - AFSC Requirements: 🎯
  - Integrity: ⚖️
  - Service: 🎖️
  - Excellence: ⭐
  - Bonus: 🏆
  - Behavioral: 📊
  - Threshold: 📈
- Section score shown as a pill/badge: `background: var(--surface-alt); padding: 2px 8px; border-radius: 4px`

### U4: Smooth Accordion (CSS Grid)
Replace the `max-height` hack with CSS Grid accordion:
```css
.section-content {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows .35s cubic-bezier(.4, 0, .2, 1);
}
.section-header[aria-expanded="true"] + .section-content {
  grid-template-rows: 1fr;
}
.section-content > .section-body,
.section-content > .threshold-section {
  overflow: hidden;
}
```

### U5: Score Controls — Polish
- Remove the gap between adjacent buttons (use `border-left: none` on non-first labels)
- Better border radius: 8px on ends
- Add hover lift: `transform: scaleY(1.04)` with subtle shadow
- Add press feedback: `transform: scale(0.96)` on `:active`
- Selected state: subtle inner shadow + slight scale up
- Add tooltips via `data-tip` attribute (0="Does not meet", 1="Below standard" for 0-3 scale, etc.)

### U6: Item Number Styling
Style item numbers as small pills:
```css
.item-number {
  font-weight: 800; color: var(--primary); font-size: .7rem;
  min-width: 1.8rem; display: inline-flex; align-items: center; justify-content: center;
  background: var(--surface-alt); border-radius: 4px;
  padding: 2px 0; flex-shrink: 0;
}
```

### U7: Hint Text Styling
Add left border to hints:
```css
.item-hint {
  padding-left: .5rem; border-left: 2px solid var(--border-light);
}
```

### U8: Threshold Visualization
- Gradient fills on the progress bar
- Better threshold markers (styled, not just text)
- Status icons: ✓ for PEP, ⚠ for meets minimum, ✗ for below

### U9: Commander's Note
Style as a formal callout box:
```css
.commanders-note {
  background: var(--surface-alt);
  border: 1px solid var(--border);
  border-left: 4px solid var(--primary);
  padding: 1rem 1.25rem;
  border-radius: 0 6px 6px 0;
  font-style: italic;
}
```

### U10: Save Indicator
Add an auto-save timestamp near the action buttons:
```html
<div id="saveIndicator" aria-live="polite" style="text-align:center;font-size:.75rem;color:var(--text-muted);padding:.25rem 0"></div>
```
Update `saveState()` to show "Auto-saved HH:MM:SS" and show warning if storage fails.

### U11: Storage Check on Load
At DOMContentLoaded, test if localStorage works and show warning if not.

## MOBILE FIXES

### M1: Safe Area Insets
Add bottom safe area padding to mobile score bar and main content:
```css
.mobile-score-bar {
  padding-bottom: calc(.6rem + env(safe-area-inset-bottom, 0px));
}
main { padding-bottom: calc(4.5rem + env(safe-area-inset-bottom, 0px)); }
```

## PRINT IMPROVEMENTS

### P1: Show AFSC Requirements in Print
Remove `#afscRequirements` from print hide list. Style AFSC requirements for print:
- Show requirement name + badge (REQUIRED/OPTIONAL) as text
- Show checkbox state as ☑ or ☐
- Clean layout matching the rest of the formal document

### P2: Ensure Print Header Works
The print header should show:
- "DEPARTMENT OF THE AIR FORCE • 934TH AIRLIFT WING (AFRC)"
- "PROMOTION ELIGIBILITY SCORING WORKSHEET"
- Member name, rank, AFSC, date

## DARK MODE

### D1: Header Dark Mode
```css
[data-theme="dark"] .site-header {
  background: linear-gradient(135deg, #0a1628 0%, #162d50 60%, #0e1f38 100%);
  border-bottom-color: #8b7332;
}
```

### D2: Score Color Adjustments for Dark Mode
Ensure score colors are readable in dark mode. The dark mode score colors are already defined but double-check contrast.

## WHAT "DONE" LOOKS LIKE

The final `index.html` must:
1. ✅ Show AFSC-specific requirements when rank + AFSC are selected
2. ✅ Sections collapse and expand smoothly when clicked
3. ✅ 934th AW emblem displayed in the header
4. ✅ All scoring calculations correct (max 48 per unit policy)
5. ✅ LocalStorage saves and restores everything including AFSC checkboxes
6. ✅ Mobile-optimized with safe area insets
7. ✅ Print produces a formal military document
8. ✅ Dark mode works
9. ✅ All accessibility fixes implemented
10. ✅ Single self-contained HTML file, no external dependencies (except the emblem image URL)
11. ✅ Polished, professional UI worthy of military use

Overwrite `index.html`. Do not leave any TODO comments.
