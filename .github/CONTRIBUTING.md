# Contributing

Thanks for your interest in helping improve Destronia AdBlock Filter — we appreciate all contributions.

This document explains how to report issues, propose changes, and submit contributions so they can be reviewed and merged quickly.

Quick links

- Report an issue: [Open an issue](https://github.com/Destronia/AdBlock_Filter/issues/new)
- Discussions: [Project discussions](https://github.com/Destronia/AdBlock_Filter/discussions)
- Pull requests: [View PRs](https://github.com/Destronia/AdBlock_Filter/pulls)
- Contributor License Agreement (CLA): [CLA Assistant](https://cla-assistant.io/Destronia/AdBlock_Filter)
- Translation platform: [Crowdin](https://crwd.in/destronia-adblock-filter)

If you plan to make code or content changes, please read the steps below.

## Before you start

- Search existing issues and discussions to avoid duplicates.
- Read the `README.md` and the repository structure (see the `filters/` directory) to understand where rules belong.
- Sign the Destronia Contributor Agreement (CLA) — we cannot accept pull requests from contributors who haven’t signed it.

- Read the `docs/rules-layout.md` file for the preferred rule layout template, examples, and the contributor checklist. It contains concrete examples and testing tips for adding or modifying filter rules.

## Filing issues

When filing a bug report or feature request, include:

- A short, descriptive title.
- A clear description of the problem or feature.
- Steps to reproduce (URL, browser, steps taken).
- Expected vs actual behavior.
- Screenshots or HTML snippets when relevant.

Use the issue templates available in the repository when possible.

## Making changes (pull requests)

Small, focused pull requests are the fastest to review. Typical contributions include:

- New or updated filter rules (add to the appropriate `filtersYYYY.txt` file).
- Fixes or clarifications to `README.md`, `CONTRIBUTING.md`, or site-specific notes.
- Tests or tooling improvements (discuss first if substantial).


Pull request checklist

- Target the `master` branch.
- Use a descriptive title, e.g. “Add block rule for example.com — fixes #123”.
- Include a short description and rationale for the change.
- For new filter rules, add a comment explaining the target site/page and why the rule is scoped as it is.
- Keep changes minimal and scoped (avoid broad element rules without site scoping).
- Ensure you have signed the CLA.

- For detailed guidance on where to place rules, example site-blocks, and a pre-submission checklist, see `docs/rules-layout.md`.


Where to add rules

- This repository keeps rules organized by year. Add new, site-specific rules to the current year file (for example, `filters2024.txt`).
- Do not duplicate rules across year files.
- The master list `filters/filters.txt` references year files; do not edit that file to remove existing includes unless instructed by maintainers.
- If you believe a new year file (for example `filters2024.txt`) is needed, do not create it yourself — open a Discussion or mention the need in your PR so maintainers can add the year file and include it in the master list.

## Style and conventions for filter rules

- Follow Adblock/uBlock syntax exactly (examples live in `filters2023.txt`).
- Prefer precise, minimal selectors scoped to a site or page rather than broad global rules.
- Add a short comment above non-obvious rules explaining the intent and the URL(s) tested.

## Translations

Translation contributions are handled via Crowdin: [Crowdin project](https://crwd.in/destronia-adblock-filter)

## Tests and validation

There is no automated test suite. Validate new or changed rules by loading the raw `filters/filters.txt` URL in an adblocker (uBlock Origin recommended) and checking the targeted site for breakage. When possible include the URL(s) you tested in your PR description.

## Code of conduct

Be respectful and constructive. Maintain a cooperative tone in issues, PRs, and discussions.


## Where to get help

- Ask maintainers or the community via Discussions: [Project discussions](https://github.com/Destronia/AdBlock_Filter/discussions)
- For CLA questions, use the CLA Assistant link above.

## A note about repository edits

This repo is data-first (filter lists). Avoid adding build systems, runtime code, or CI unless you’ve discussed changes with maintainers first. Keep diffs small and focused.

---

If something in this guide is unclear or you want to contribute a large change, open a discussion first and we’ll help you plan it.

Thanks for contributing!
