The Destronia AdBlock Filter repository is a collection of text-based AdBlock rules and site-specific selectors
organized by year. The goal for contributors (and AI agents) is to maintain correct, minimal, and well-scoped
filter rules that safely block ads without breaking site functionality.

Key things an AI agent should know before editing:

- Project layout (important files):
  - `filters/filters.txt` — top-level list that includes year-based sublists. Changes here control the published
    master list and should only add or include sublists, or update header metadata (Version, Title, Expires).
  - `filters/filtersYYYY.txt` — year-scoped rule files (examples: `filters2021.txt`, `filters2022.txt`, `filters2023.txt`).
    These contain the actual filter rules (Adblock syntax). Prefer adding new rules to the relevant year file.
  - `README.md` — user-facing installation & contribution guidance. Keep consumer-facing language accurate.
  - `VERSION` — simple plaintext semantic version used for releases; update this when publishing a new release.
  - `docs/_config.yml` — Jekyll site config for docs; generally not changed for filter edits.

  - See `docs/rules-layout.md` for the preferred rule layout template, concrete examples, and a contributor checklist; automated agents should follow that guide when adding or editing filter rules.

- Edit rules, not behavior: this repo is data-first (filter lists). Avoid adding build systems or runtime code unless
  required for automation (discuss first). Keep diffs to the minimum necessary (single-rule additions in year files).

- Style and conventions specific to this project:
  - New filters are placed into the year-based files (see header in `filters/filters.txt`). Do not duplicate rules across years.
  - Header comments in `filters/filters.txt` follow this format:
  - `! Version: 9.1.0`  # replace with actual semver when updating
  - `! Title: Destronia General Filters`
  - `! Last modified: 21 February 2023 14:37 (UTC)`  # use current UTC date when updating
  - `! Expires: 4 days`
  - The master `filters/filters.txt` references year files via an include line; for example the master list will reference `filters2023.txt`. When adding a new yearly list, add that filename to the master list.
  - Use adblock/uBlock filter syntax exactly (examples present in `filters2023.txt`). Preserve whitespace and comment markers (`!`).

- When updating `VERSION` and `filters/filters.txt` headers:
  - Bump `VERSION` to the new semver (follow existing format in the `VERSION` file).
  - Update the `! Version:` header in `filters/filters.txt` to match.
  - Update `! Last modified:` to the current date in UTC and `! Expires:` if appropriate.

- Testing and validation (manual):
  - There is no automated test suite. Validate new rules locally by loading the raw `filters/filters.txt` URL in an adblocker
    (uBlock Origin recommended) and checking the targeted site for breakage. For minor selector edits, prefer adding a comment
    explaining why the rule is needed and which site/page it targets.

- Pull request guidance for AI agents:
  - Keep PRs small and focused (single-site or small related rule sets). Use PR title like: Add block rule for example.com — fixes issue 123 (replace 123 with the issue number).
  - In PR description include: rationale, which site/version was tested, and a short reproduction (URL and element targeted).

- Avoid risky changes:
  - Do not wholesale remove large sections of rules or introduce broad, generic blocking tokens (e.g., blanket element rules without site scope).
  - Do not add scripts, binaries, or CI pipelines; discuss with maintainers first.

Examples from this repo:
- Adding a rule for a new site in 2024 would mean adding an entry to `filters/filters2024.txt` and adding an `!#include filters2024.txt`
  line to `filters/filters.txt` if not already included.
- To update the release version to 9.2.0, edit `VERSION` to `9.2.0` and set `! Version: 9.2.0` in `filters/filters.txt` and update
  `! Last modified:` to the current UTC date.

If any part of the repo's purpose looks unclear or you need permission to change the publishing process (releases or CDN URLs),
ask a maintainer instead of guessing.
