# Editing Guide — kanhabatra.github.io

This guide covers every content update you will ever need to make.
No HTML, no CSS, no Ruby knowledge required.

---

## Quick reference

| What you want to change                         | File to edit               |
| ----------------------------------------------- | -------------------------- |
| Name, institution, site URL                     | `_config.yml`              |
| Bio / about text                                | `_pages/about.md`          |
| Social links (email, Scholar, LinkedIn, GitHub) | `_data/socials.yml`        |
| Publications                                    | `_bibliography/papers.bib` |
| News / announcements                            | `_news/`                   |
| Research projects                               | `_projects/`               |
| CV (education, jobs, skills, awards)            | `assets/json/resume.json`  |
| Profile photo                                   | `assets/img/prof_pic.jpg`  |
| CV PDF                                          | `assets/pdf/cv.pdf`        |
| GitHub repos shown on Repositories page         | `_data/repositories.yml`   |

---

## 1. Fill in your personal details

Open `_config.yml`. The top section has everything site-wide:

```yaml
first_name: Kanha
last_name: Batra
url: https://kanhabatra.github.io
baseurl: ""
```

Open `_data/socials.yml` and fill in your IDs:

```yaml
email: your@email.com
github_username: kanhabatra
scholar_userid: XXXXXXXXXXXX # from your Google Scholar URL
linkedin_username: your-name # from linkedin.com/in/your-name
```

To find your **Google Scholar ID**: go to your Scholar profile page →
the URL will look like `scholar.google.com/citations?user=XXXXXXXXXXXX` — copy that `user=` value.

---

## 2. Update your bio

Open `_pages/about.md`. Everything below the `---` line is plain text with
[Markdown formatting](https://www.markdownguide.org/basic-syntax/).
Edit it like a document. The YAML block at the top controls the profile card:

```yaml
subtitle: "Postdoctoral Fellow · My Institution"
profile:
  more_info: >
    <p>📍 City, Country</p>
    <p>🏛️ Department</p>
```

---

## 3. Add a publication

Open `_bibliography/papers.bib`.

**Step 1** — get the BibTeX entry for your paper. On Google Scholar,
click "Cite" → "BibTeX" under any paper. On arXiv, click "Export BibTeX citation".

**Step 2** — paste it into `papers.bib`.

**Step 3** — add al-folio extras inside the entry `{ }` to enrich the card:

```bibtex
@article{batra2025mypaper,
  title   = {My Paper Title},
  author  = {Batra, Kanha and Collaborator, A.},
  journal = {Nature Neuroscience},
  year    = {2025},

  % --- al-folio extras (all optional) ---
  selected          = {true},        % shows on homepage
  abstract          = {Your abstract text here.},
  pdf               = {batra2025mypaper.pdf},   % drop PDF in assets/pdf/
  html              = {https://doi.org/...},
  arxiv             = {2501.00000},
  code              = {https://github.com/kanhabatra/...},
  google_scholar_id = {XXXXXXXXXX},  % enables live citation count badge
}
```

Only entries with `selected = {true}` appear on the homepage.
All entries appear on the Publications page, grouped by year.

---

## 4. Add a news announcement

Create a new file in `_news/`, e.g. `_news/2025_neurips.md`:

```markdown
---
layout: post
date: 2025-09-25 09:00:00-0400
inline: true # true = one-line; false = full expandable post
related_posts: false
---

Paper accepted at NeurIPS 2025! Preprint coming soon.
```

For a longer announcement (e.g. a talk summary), set `inline: false` and
write as many paragraphs as you like below the `---`.

---

## 5. Update a research project

Each file in `_projects/` is one project card. The YAML header controls the card:

```yaml
---
title: My Project
description: Short one-line description shown on the card.
img: assets/img/projects/my_project.png # optional thumbnail
importance: 1 # lower = appears first
category: research # used for filtering
---
```

Below the `---`, write normally in Markdown. You can include equations
with LaTeX: `$E = mc^2$` inline, or `$$...$$` for display math.

To add a new project: copy one of the existing `.md` files, rename it
`_projects/4_new_project.md`, and edit the content.

---

## 6. Update your CV

Open `assets/json/resume.json`. It is structured JSON — edit the values
between the `" "` quotes. The sections are:

- `basics` — name, email, location summary
- `work` — positions (postdoc, RA, etc.) — add an object per role
- `education` — degrees, advisor, thesis title
- `awards` — fellowships, prizes
- `skills` — technical skills with keywords
- `publications` — key publications (separate from the BibTeX page)

**To add a new job/position**, copy an existing block in `"work"`:

```json
{
  "name": "New Institution",
  "position": "Research Scientist",
  "location": "City, Country",
  "startDate": "2026-01-01",
  "endDate": "",
  "summary": "What you did.",
  "highlights": ["Achievement 1", "Achievement 2"]
}
```

---

## 7. Upload your profile photo

Drop any JPG or PNG file named `prof_pic.jpg` into `assets/img/`.
The site will pick it up automatically.

---

## 8. Upload your CV PDF

Drop your CV as `cv.pdf` into `assets/pdf/`.
The social icon in `_data/socials.yml` already points to `/assets/pdf/cv.pdf`.

---

## 9. Deploying changes

Every time you push to GitHub, the site rebuilds automatically (< 2 min).

**From GitHub Desktop** (recommended):

1. Open GitHub Desktop → it shows your changed files
2. Write a short commit message (e.g. "Add NeurIPS paper")
3. Click **Commit to main** → **Push origin**

**From Terminal** (if you prefer):

```bash
git add -A
git commit -m "Add NeurIPS paper"
git push
```

---

## 10. Local preview (optional, requires Ruby)

If you want to preview changes before pushing:

```bash
# Install dependencies once
bundle install

# Serve locally
bundle exec jekyll serve

# Open http://localhost:4000 in your browser
```

See `INSTALL.md` for full setup instructions including the Docker option
(no Ruby install needed).

---

## Still stuck?

- Full al-folio documentation: https://github.com/alshedivat/al-folio
- Jekyll docs: https://jekyllrb.com/docs/
- Markdown reference: https://www.markdownguide.org/basic-syntax/
