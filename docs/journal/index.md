# GitHub Website — Journal Index

## Core goals

- Maintain Kanha Batra's academic personal website (al-folio Jekyll theme) as an accurate, up-to-date presence: bio, news, publications, projects, CV.
- Keep the site building and deploying cleanly via the GitHub Pages Actions pipeline (`.github/workflows/deploy.yml`).
- Keep content (pages, projects, news, bibliography, CV data) current and consistent with `_config.yml` and the al-folio conventions documented in `AGENTS.md`.

## Key ideas

- Site is a fork/instance of the upstream al-folio theme; upstream docs (`README.md`, `INSTALL.md`, `CUSTOMIZE.md`, `TROUBLESHOOTING.md`) and repo-specific `AGENTS.md` are the primary references before making structural changes.
- Docker (`docker compose up`) is the documented local dev loop; production deploy is a separate GitHub Actions pipeline that builds with Jekyll directly (not the Docker image).
- CV content lives in `_data/cv.yml` and is rendered by a dedicated workflow (`render-cv.yml`), so CV updates start in YAML, not in a hand-edited output file.

## Log summary table

| File | Period | Summary | Status | Weight |
|------|--------|---------|--------|--------|
| [2026-07](2026-07.md) | July 2026 | Documentation scaffold created; captured current-state snapshot of repo layout, build, and deploy. | open | 2 |

## Scratch

(none yet)
