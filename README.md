# Giada Durante — Academic Website

Built with [Quarto](https://quarto.org). Clean, minimalist academic design.

---

## Prerequisites

Install Quarto: https://quarto.org/docs/get-started/

Verify it is installed:
```bash
quarto --version
```

---

## 1. Preview the site locally

Open a terminal in this folder and run:

```bash
quarto preview
```

This starts a local server (usually at http://localhost:4848) and live-reloads
whenever you save a file. Press Ctrl+C to stop.

To do a one-shot render without the live server:
```bash
quarto render
```
The output goes to the `_site/` folder.

---

## 2. Editing pages

Each page is a `.qmd` file (Quarto Markdown — plain Markdown with optional HTML):

| File | Page |
|---|---|
| `index.qmd` | Home / bio |
| `research.qmd` | Research papers |
| `teaching.qmd` | Teaching |
| `cv.qmd` | CV (download + embed) |
| `contact.qmd` | Contact info |

Open any file in a text editor and look for the `<!-- Edit ... -->` comments —
they mark every section you will want to update. Save the file and the preview
auto-refreshes.

**Site-wide settings** (title, navbar, footer, fonts, colors) are in:
- `_quarto.yml` — Quarto configuration
- `styles/theme.scss` — custom CSS (colors, typography, card styles)

---

## 3. Adding content

### Adding or updating your headshot

1. Save your photo as `images/profile.jpg` (or `.png`).
2. Open `index.qmd` and change the `src` attribute:
   ```html
   <img src="images/profile.jpg" ...>
   ```

### Updating your CV

1. Export your CV as a PDF.
2. Save it as `files/cv.pdf` (replace the placeholder file if one exists).
3. Run `quarto render` — the download button and embedded viewer update automatically.

### Adding a research paper

Open `research.qmd` and copy the template block at the bottom of the file.
Paste it inside the `## Work in Progress` section and fill in:
- `paper-title` — the title
- `paper-authors` — authors (your name in `<strong>`)
- `paper-status` — e.g. `Work in Progress`, `Job Market Paper`, `Submitted`
- `paper-abstract` — replace the placeholder text
- Uncomment the `<a>` links when draft/slides are ready; place PDFs in `files/`

### Adding teaching materials

1. Save files (syllabus, slides, problem sets) to the `files/` folder.
2. Open `teaching.qmd`, find the relevant course card, and uncomment the `<a>` links,
   updating the `href` paths to match your filenames.

---

## 4. Deploying to GitHub Pages (when ready)

### Step 1 — Create a GitHub repository

```bash
git init
git add .
git commit -m "Initial website"
```

Go to https://github.com/new and create a repository (e.g. `academic-website`).

```bash
git remote add origin https://github.com/YOUR_USERNAME/academic-website.git
git push -u origin main
```

### Step 2 — Publish with Quarto

Quarto has a built-in publish command that pushes your rendered site to the
`gh-pages` branch automatically:

```bash
quarto publish gh-pages
```

Follow the prompts. Your site will be available at:
`https://YOUR_USERNAME.github.io/academic-website/`

### Step 3 — Connect a custom domain (giadadurante.com)

1. The `CNAME` file in this project already contains `giadadurante.com`.
   Quarto's publish command copies it to `_site/` and pushes it to `gh-pages`.

2. In your GitHub repository → **Settings → Pages → Custom domain**,
   enter `giadadurante.com` and save.

3. Configure DNS at your domain registrar:

   | Type | Name | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | CNAME | www | YOUR_USERNAME.github.io |

   DNS propagation can take up to 24–48 hours.

4. Once propagated, enable **Enforce HTTPS** in GitHub Pages settings.

**Reference:** https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

---

## Project structure

```
academic-website/
├── _quarto.yml          # Site configuration (title, navbar, theme)
├── index.qmd            # Home page
├── research.qmd         # Research papers
├── teaching.qmd         # Teaching
├── cv.qmd               # CV download + embed
├── contact.qmd          # Contact info
├── styles/
│   └── theme.scss       # Custom CSS overrides
├── images/
│   └── profile.svg      # Profile photo placeholder → replace with your photo
├── files/
│   └── .gitkeep         # Place CV and paper PDFs here
├── CNAME                # Custom domain for GitHub Pages
├── .gitignore
└── README.md
```
