# Multi-Scale Modelling (MSM) · ZALF — group website

Website of the **Multi-Scale Modelling (MSM)** working group, Research Area 4 “Simulation and Data Science”,
Leibniz Centre for Agricultural Landscape Research (ZALF).

Built with [Quarto](https://quarto.org/) on the framework of
[blenback.github.io](https://github.com/blenback/blenback.github.io). The stack, file structure and design are the same:

| Layer | Files |
|---|---|
| Brand (colours, fonts) | `_brand.yml` |
| Component styles | `theme.scss` (framework styles + “MSM COMPONENTS” section) |
| Site config, navbar, SEO | `_quarto.yml` |
| Includes | `header.html` (fonts/meta), `nav-scroll.html` (transparent→solid navbar), `msm-footer.html` (footer) |
| Listing templates | `ejs/*.ejs` |
| **Content (edit these)** | `team/members.yml`, `projects/projects.yml`, `publications/*.yml`, `news/*.qmd`, `news/talks.yml`, `jobs/jobs.yml`, `research/themes.yml` |
| Pages | `index.qmd`, `about.qmd`, `research.qmd`, `team.qmd`, `projects.qmd`, `publications.qmd`, `news.qmd`, `jobs.qmd`, `contact.qmd` |

## Editing content

All content lives in YAML/Markdown files. You never need to touch HTML/CSS to keep the site up to date.
Every data file starts with a comment block describing its fields and a copy-paste **TEMPLATE**.

> **Note:** do not put HTML tags inside YAML values (Quarto escapes them). Use plain text and Unicode (e.g. `CO₂`).

| Task | Do this |
|---|---|
| **Add a team member** | Copy the template at the bottom of `team/members.yml`. Put a photo (square, ≥ 600 px) in `assets/team/`. For a full profile page, copy `team/srivastava.qmd` and set `page:`. |
| **Remove / move to alumni** | Delete the block, or set `group: "Alumni"`. |
| **Add a project** | Add a block to `projects/projects.yml`. *Ongoing/Completed* is computed from `end:`; `featured: true` shows it on the home page. |
| **Add a publication** | Add a block at the top of `publications/journal-articles.yml` (or `books-reports.yml`, `conference-contributions.yml`). Use the full `https://doi.org/…` URL. |
| **Highlight a new member's name in publications** | Extend `MEMBER_NAMES` in `ejs/publication_filter.ejs` and `ejs/publication_yearly_home.ejs`. |
| **Post news** | Copy any file in `news/`, rename it `YYYY-MM-DD-short-title.qmd`, edit the front matter + text. Thumbnails: `assets/news/`. |
| **Add a talk** | Add a block to `news/talks.yml`. |
| **Advertise a job** | Replace `[]` in `jobs/jobs.yml` with entries (see template). On their `deadline`, adverts move to “Past opportunities” automatically. |
| **Contact persons** | Set `contact: true` on a member in `team/members.yml`. |

Publications support deep links, e.g. `publications.html?q=machine+learning&type=article&year=2025`.

## Local preview

```bash
quarto preview          # live preview
quarto render           # builds the site into docs/
```

## Deployment (GitHub Pages)

1. Create a repository and push this folder to the `main` branch.
2. In `_quarto.yml`, set `site-url:` to the final URL. Update the `Sitemap:` line in `robots.txt` to match.
3. **Recommended: GitHub Actions.** `.github/workflows/publish.yml` renders the site and pushes it to the `gh-pages` branch on every push. It also rebuilds weekly, so project and job statuses stay current.
   Under *Settings → Pages*, choose **Deploy from a branch → `gh-pages` / root**.
4. *Alternative:* commit the rendered `docs/` folder and choose **Deploy from a branch → `main` / `docs`**.

The site works both as a user/organisation site (`<name>.github.io`) and as a project site (`<name>.github.io/<repo>/`).

## Accessibility, performance & SEO

- WCAG-AA contrast for text colours, a visible keyboard focus, a skip link, `prefers-reduced-motion` support and labelled controls.
- The site is static and needs no build-time R or Python. Images are lazy-loaded.
- Per-page `description`, Open Graph and Twitter cards (`assets/og-image.png`), plus an automatic `sitemap.xml`, `robots.txt` and an RSS feed (`news.xml`).
- No third-party embeds or trackers. Maps link out to OpenStreetMap, which helps with GDPR.

## Content sources

The site's content comes from the group documents (`documents/msm`) and the official
[ZALF working-group page](https://www.zalf.de/en/struktur/pb4/Pages/Arbeitsgruppen.aspx#x90x), as of 22 Nov 2026.
