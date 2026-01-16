![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/Destronia/AdBlock_Filter?style=flat-square)
[![GitHub license](https://img.shields.io/github/license/Destronia/AdBlock_Filter?style=flat-square)](https://github.com/Destronia/AdBlock_Filter/blob/master/LICENSE)
![GitHub forks](https://img.shields.io/github/forks/Destronia/AdBlock_Filter?style=social)
![GitHub Repo stars](https://img.shields.io/github/stars/Destronia/AdBlock_Filter?style=social)
[![CodeFactor](https://www.codefactor.io/repository/github/destronia/adblock_filter/badge)](https://www.codefactor.io/repository/github/destronia/adblock_filter)
[![Crowdin](https://badges.crowdin.net/destronia-adblock-filter/localized.svg)](https://crowdin.com/project/destronia-adblock-filter)
[![Documentation Status](https://readthedocs.org/projects/adblock-filter/badge/?version=latest)](https://adblock-filter.readthedocs.io/en/latest/?badge=latest)

# Destronia AdBlock Filter

A curated set of AdBlock/uBlock/AdGuard filter rules maintained by the Destronia community. The repository is data-first — it stores filter lists and per-site rules organized by year.

## Quick install

1. Open your adblocker's dashboard (for uBlock Origin: Dashboard → Filter lists → 3rd-party filters).
1. Add this raw list URL as a third-party filter:

  [Raw filters.txt on GitHub](https://raw.githubusercontent.com/Destronia/AdBlock_Filter/master/filters/filters.txt)

1. Enable the list and refresh/update filters in your blocker.

If you prefer a step-by-step guide for uBlock Origin, see the uBlock Origin docs: [Dashboard - Filter lists (3rd-party filters)](https://github.com/gorhill/uBlock/wiki/Dashboard:-Filter-lists#3rd-party-filter-lists/)

## Files and structure

- `filters/filters.txt` — master list that includes year-based rule files.
- `filters/filtersYYYY.txt` — year-scoped rule files (e.g. `filters2021.txt`).
- `VERSION` — release version used for publishing.
- `docs/` — documentation and contributor guides.

Additions and edits should usually be made to the appropriate `filters202X.txt` file for the year of the change.

## Contributing

We welcome contributions. Small PRs are preferred (single-site or small related rule sets).

Steps to contribute a new rule:

1. Add the rule to the appropriate year file under `filters/` (create `filters2026.txt` if adding current-year rules).
2. Include a short comment explaining the site/page targeted and why the rule is safe (see `docs/rules-layout.md`).
3. Update `filters/filters.txt` only when adding a new year file — add an `!#include filters2026.txt` line and bump headers (see repo guidance).
4. Open a PR with a concise title (for example: "Add block rule for example.com — fixes issue 123") and include test steps and a brief rationale.

See the full contributing guide: .github/CONTRIBUTING.md

## Troubleshooting

- If ads still appear after enabling the list, force a manual update in your blocker and clear the browser cache.
- If a site breaks after applying a rule, open an issue with the URL, a short description, and which rule you suspect.

## Recommended blockers

- uBlock Origin — lightweight and configurable: [uBlock Origin](https://github.com/gorhill/uBlock)
- AdGuard — privacy-focused blocker with GUI apps: [AdGuard](https://github.com/AdguardTeam)

## Contributors ✨

Thanks goes to these wonderful people:

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://destronia.com"><img src="https://avatars.githubusercontent.com/u/54786587?v=4?s=100" width="100px;" alt=""/><br /><sub><b>redtrillix</b></sub></a><br /><a href="https://github.com/Destronia/AdBlock_Filter/commits?author=redtrillix" title="Documentation">📖</a> <a href="https://github.com/Destronia/AdBlock_Filter/commits?author=redtrillix" title="Code">💻</a> <a href="https://github.com/Destronia/AdBlock_Filter/commits?author=redtrillix" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/JakeWasHere2"><img src="https://avatars.githubusercontent.com/u/63701873?v=4?s=100" width="100px;" alt=""/><br /><sub><b>JakeWasHere2</b></sub></a><br /><a href="https://github.com/Destronia/AdBlock_Filter/commits?author=JakeWasHere2" title="Documentation">📖</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

---

This page is a work in progress. See `.github/CONTRIBUTING.md` for documentation contribution instructions.
