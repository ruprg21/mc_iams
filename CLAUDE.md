# CLAUDE.md

## Project

Single-file HTML dashboard: `mcc_idealams_workflow.html`
Covers MCC IdealAMS system architecture — EPICs, integrations, candidate journey.

## File structure

Everything is in one file — CSS, HTML, and JS are all inline. No build system, no dependencies, no package.json.

## Working with this file

- All styles are in a `<style>` block in `<head>`
- All data (EPICs, integrations, journey steps) is defined as JS arrays/objects near the bottom of the file, before the closing `</body>`
- The render functions (`renderEpics()`, `renderIntegrations()`, `renderJourney()`) generate HTML from those data arrays
- Tab switching is handled by `sw(view, el)` — it shows/hides `.view` divs

## Design system

Colors follow the Salesforce Lightning palette via CSS custom properties (defined in `:root`). Key variables:
- `--sf-blue` — primary action color
- `--sf-teal`, `--sf-purple`, `--sf-orange`, `--sf-green` — category accent colors
- `--surface`, `--bg`, `--border` — layout neutrals

## What to be careful about

- Do not introduce external JS libraries or framework dependencies — this file must remain self-contained and open directly in a browser
- Keep the CSS custom properties consistent when adding new color variants
- When adding new EPICs or integrations, follow the existing data object shape exactly — the render functions expect specific keys
