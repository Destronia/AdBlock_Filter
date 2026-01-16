# Destronia filter rules layout and template

This document describes the preferred layout, conventions, and example templates for adding or editing filter rules in the Destronia AdBlock Filter repository.

Keep contributions small and focused. Add new site-specific rules to the appropriate year file under `filters/` (for example `filters2024.txt`). Do not duplicate the same rule across multiple year files.

## File responsibilities

- `filters/filters.txt` — master list that contains header metadata and includes year-scoped files via `!#include` lines. Only change this file to add a new yearly include or to update header metadata (Version, Last modified, Expires).
- `filters/filtersYYYY.txt` — year-based rule files that hold the actual AdBlock/uBlock rules. New rules should be placed in the year file matching the year when the rule was added/approved.
- `VERSION` — bump this when publishing a new release; keep the file content as a single semver string (for example `9.2.0`). When you update `VERSION`, also update the `! Version:` header in `filters/filters.txt` and the `! Last modified:` timestamp.

### Header format for `filters/filters.txt`

Keep the top-of-file header exactly like the repository convention. Update only the fields that need updating.

Example header:

```text
! Version: 9.1.0
! Title: Destronia General Filters
! Last modified: 21 February 2023 14:37 (UTC)
! Expires: 4 days
```

When releasing a new version:
- Update `VERSION` to the new semver.
- Update the `! Version:` line in `filters/filters.txt` to match `VERSION`.
- Update `! Last modified:` to the current UTC date/time.
- Keep `! Expires:` as appropriate for the project (usually `4 days`).

### Year file layout (`filters/filtersYYYY.txt`)

Each year file should group related rules and provide short comments explaining non-obvious selectors or site-targeting. Prefer specific, minimal selectors to avoid breaking site functionality.

Suggested structure inside a year file:

1. Short header comment with year and brief purpose
   - Example: `! Destronia filters added in 2024`
2. One or more site blocks. Each site block should start with a clear comment describing the site/page and reason.
3. Minimal rules scoped to the site using domain anchors or element selectors.
4. Optional test notes or a small reproduction snippet showing the page/element targeted.

Example site block:

```text
! example.com — blocks sticky promo banner on homepage
! Tested: `https://example.com/` (Jan 2026)
! Selector: .promo-sticky
example.com##.promo-sticky

! example.com##.promo-sticky:style(display: none !important)
```

Notes:
- Prefer domain-limited cosmetic rules (`example.com##selector`) over global element rules.

- Avoid rules like `##.ad` or `##div[id^="ad"]` without site scoping.

- When a rule must be global (rare), include a clear justification comment.

### Rule style and syntax quick reference

- Block network requests: `||example.com^` or `||example.com^$third-party`
- Element hiding: `example.com##.classname` or `example.com,another.com##.classname` for multiple domains
- CSS style rule (uBO): `example.com##.classname:style(display: none !important)`
- Script or redirect-based exceptions: use `$script,domain=example.com` modifiers where appropriate

### Small checklist for new rules (use before opening a PR)

- Is the rule scoped to a domain or page? If not, add a justification comment.
- Will this rule break site functionality? Test interactive pages and log any regressions.
- Add a short reproduction URL and a short note on what the rule hides/blocks.
- Place the rule in the current year file. If you're adding many rules spanning years, discuss with maintainers.
- If releasing immediately, update `VERSION` and the `filters/filters.txt` header.

### Testing recommendations

- Load the raw `filters/filters.txt` into uBlock Origin (Dashboard → My Filters → Import from file/raw) to test locally.
- Test the minimal set of pages affected; check functionality like login, checkout, video playback, and site navigation.
- If a rule causes breakage, narrow the selector or change it to a more specific subtree.

### Example contribution PR description template

Title: Add block for example.com sticky promo — fixes #123

Body:

- Rationale: Blocks persistent sticky promo banner that obscures content on the homepage.
- Files changed: `filters/filters2026.txt` (added 1 rule)
- Tested: `https://example.com/` — homepage (Jan 2026) in Firefox 117 with uBlock Origin
- Reproduction: The `.promo-sticky` element appears after page load and stays fixed at the bottom, covering buttons.

---

If you are unsure about a change that might be risky (broad cosmetic rules, domain-wide network blocks), open an issue or ask maintainers for a review before submitting a large PR.

---

Thank you for contributing — small, well-documented changes keep the list reliable and safe for users.
