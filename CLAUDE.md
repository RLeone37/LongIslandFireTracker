# Claude Code Instructions

- Always bump the patch version in index.html, README.md, and CHANGELOG.md when making changes
- Update the relevant tab description in README.md if the change affects a tab's behavior
- Add a dated entry to CHANGELOG.md for every index.html change
- .gitignore is present — do not commit node_modules or other ignored files
- `fires.json` data-only fixes can be committed directly to `main`
- Version format is `vMAJOR.MINOR.PATCH` — bug fixes and cosmetic changes are PATCH only
