# GitHub Website — Project Blueprint
Kanha Batra's academic personal website: an al-folio Jekyll theme instance, published as a GitHub Pages site.

## Overview

The repository is a fork/instance of the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme, configured for Kanha Batra (postdoctoral fellow, computational neuroscience and AI). Its purpose is to serve as a personal academic homepage: bio, news, publications, projects, CV, and blog.

- Site title/author: `first_name: Kanha`, `last_name: Batra` (`_config.yml`, lines 6-7)
- Site URL: `https://kanhabatra.github.io`, `baseurl: ""` (root/personal site) (`_config.yml`, lines 19-20)
- Deploy target: GitHub Pages, served via the official `actions/deploy-pages` GitHub Action (see Build & deploy below).

## Repository layout

| Path | Purpose |
|------|---------|
| `_pages/` | Top-level site pages (`about.md`, `blog.md`, `cv.md`, `news.md`, `projects.md`, `publications.md`, `404.md`). |
| `_projects/` | Project write-ups, one file per project (e.g. `1_neural_dynamics.md`, `5_medical_imaging.md`); numeric prefixes control ordering. |
| `_news/` | Short news/announcement snippets shown on the news page (`announcement_1.md`, etc.). |
| `_data/` | Structured YAML data: `citations.yml`, `coauthors.yml`, `cv.yml` (CV source of truth), `repositories.yml`, `socials.yml`, `venues.yml`. |
| `_bibliography/` | BibTeX publication list, `papers.bib`, rendered by `jekyll-scholar`. |
| `_includes/` | Reusable Liquid partials/components used across layouts. |
| `_layouts/` | Page/post layout templates. |
| `_sass/` | Theme styling (SCSS partials). |
| `assets/` | Static assets — images, CV render pipeline config (`assets/rendercv/`), JS, etc. |
| `_config.yml` | Site-wide configuration: metadata, theme options, plugin list, `exclude`/`keep_files`. |
| `Gemfile` / `Gemfile.lock` | Ruby/Jekyll dependency manifest (Jekyll core plus theme plugins such as `jekyll-scholar`, `jekyll-archives-v2`, `jekyll-paginate-v2`, `jekyll-sitemap`). |
| `Dockerfile`, `docker-compose.yml`, `docker-compose-slim.yml` | Local development containers (Ruby/Jekyll image, dev server on port 8080). |
| `.github/workflows/` | CI/CD: `deploy.yml` (build + publish to GitHub Pages), `render-cv.yml` (regenerate CV from `_data/cv.yml` via RenderCV), `update-citations.yml`, `codeql.yml`, `prettier.yml`, `axe.yml`, `broken-links-site.yml`. |
| `.github/copilot-instructions.md`, `.github/agents/`, `.github/instructions/` | Coding-agent guidance referenced from `AGENTS.md` (tech stack, per-filetype instructions, customization/docs agents). |
| `bin/entry_point.sh` | Container entrypoint used by the Docker dev server. |
| `requirements.txt` | Python dependencies for `render-cv.yml` (RenderCV, nbconvert). |

## Build & deploy

- **Local development:** Docker is the documented approach (per `AGENTS.md`). `docker compose pull && docker compose up` starts a dev server at `http://localhost:8080`; `docker compose up --build` after Gemfile/Dockerfile changes; `docker compose down` to stop.
- **Production deploy:** GitHub Actions workflow `.github/workflows/deploy.yml` ("Deploy site"), triggered on push to `master`/`main` (path-filtered to content/asset/config changes) or manual `workflow_dispatch`. It sets up Ruby and Python, patches `giscus.repo` in `_config.yml`, runs `bundle exec jekyll build` with `JEKYLL_ENV=production`, purges unused CSS with `purgecss`, then publishes `_site` via `actions/configure-pages` + `actions/upload-pages-artifact` + `actions/deploy-pages` — i.e. deploy target is GitHub Pages, not the Docker image.
- **CV rendering:** `.github/workflows/render-cv.yml` regenerates the CV from `_data/cv.yml` and `assets/rendercv/*.yaml` using RenderCV (`pip install -r requirements.txt`) whenever those files change, and commits the rendered output back to the branch.
- The Docker image (`Dockerfile`, based on `ruby:slim`) and `docker-compose*.yml` are for local development only, per `AGENTS.md`'s "Local Development (Docker)" section; no workflow in `.github/workflows/` builds or pushes this Docker image as the deploy path.

## Content conventions

Per `AGENTS.md` and the per-filetype instruction files it references (`.github/instructions/`):

- **Markdown content** (`_pages/`, `_projects/`, `_news/`, etc.) — see `.github/instructions/markdown-content.instructions.md`.
- **YAML config** (`_config.yml`, `_data/`) — see `.github/instructions/yaml-configuration.instructions.md`. When editing `_config.yml`, `url`/`baseurl` must be kept consistent (personal site: `baseurl` empty; project site: `baseurl: /repo-name/`), and strings with special characters (e.g. `title: "My: Cool Site"`) must be quoted.
- **BibTeX** (`_bibliography/papers.bib`) — see `.github/instructions/bibtex-bibliography.instructions.md`. Publications are rendered via `jekyll-scholar`.
- **Liquid templates** (`_includes/`, `_layouts/`) — see `.github/instructions/liquid-templates.instructions.md`.
- **JavaScript** (`_scripts/`) — see `.github/instructions/javascript-scripts.instructions.md`.
- **Commit format / Git practices** — see `.github/GIT_WORKFLOW.md`.
- **Pre-commit checklist** (per `AGENTS.md`): run `npx prettier . --write`, then rebuild with `docker compose up --build` and manually verify navigation, pages, images, and dark mode at `http://localhost:8080` before committing.
- News items go in `_news/` as individual files; projects go in `_projects/` with numeric-prefix filenames controlling display order; the CV page (`_pages/cv.md`) is driven by `_data/cv.yml`.

## Key artifacts

- `_config.yml` — site metadata (title, name, description, URL/baseurl, theme options), `exclude`/`keep_files` lists, and the enabled Jekyll plugin list (`jekyll-scholar`, `jekyll-archives-v2`, `jekyll-paginate-v2`, `jekyll-sitemap`, `jekyll-feed`, etc.).
- `_bibliography/papers.bib` — publication records rendered on the publications page.
- `_data/cv.yml` — CV source of truth, rendered to a PDF/asset via RenderCV (`render-cv.yml` workflow) using settings under `assets/rendercv/`.
- `_data/citations.yml`, `_data/coauthors.yml`, `_data/repositories.yml`, `_data/socials.yml`, `_data/venues.yml` — supporting structured data feeding various pages/components.

## Related documentation

- Journal index: [journal/index.md](journal/index.md)
- Current period log: [journal/2026-07.md](journal/2026-07.md)
- `AGENTS.md` (repo root) and `README.md` (repo root) remain the authoritative repo guides for agents and contributors; this blueprint summarizes and cross-references them but does not replace them. Also see `INSTALL.md`, `CUSTOMIZE.md`, `TROUBLESHOOTING.md`, `QUICKSTART.md`, and `.github/copilot-instructions.md` for deeper detail.

## Design decisions

- **al-folio template base:** the site is built on the al-folio Jekyll theme rather than a custom theme, trading some customization overhead for a maintained academic-site feature set (publications via BibTeX/jekyll-scholar, CV rendering, news feed, project pages, dark mode, search).
- **GitHub Pages deploy via Actions, not a static Docker deploy:** the Docker setup (`Dockerfile`, `docker-compose.yml`) exists solely for local development parity; production publishing goes through `bundle exec jekyll build` inside `deploy.yml` and GitHub's official Pages actions, keeping the deploy path independent of any container registry.
- **CV as generated artifact:** the CV is authored as structured data (`_data/cv.yml`) rather than a hand-maintained PDF/markdown page, and is rendered by a dedicated workflow (RenderCV) so the displayed CV stays in sync with the YAML source.
- **Personal (root) site, not a project site:** `baseurl` is empty and `url` points at the root `kanhabatra.github.io`, consistent with a personal/user GitHub Pages site rather than a project subpath site.

## Blueprint divergences

None.

## Consolidation history

None yet.
