# Website Update Cheat Sheet

## The Basic Workflow

Every update follows this pattern:

```bash
cd /Users/alexanderross/Desktop/website
# 1. Make your edits (see below)
# 2. Render the site
quarto render
# 3. Push to GitHub
git add .
git commit -m "Brief description of change"
git push
```

Changes go live within 1-2 minutes.

---

## Common Tasks

### Update Your CV
1. Update your CV and save as `Alex_CV.pdf`
2. Copy it to `files/Alex_CV.pdf` (replace the old one)
3. Run the workflow above

---

### Add a New Publication
1. Open `projects.qmd` in any text editor
2. Add under the `## Publications` section:

```markdown
**Paper Title Here**
With Coauthor Name. *Journal Name*, Year.
[[DOI]](https://doi.org/xxxxx)
```

3. Save and run the workflow above

---

### Add a New Working Paper
1. Open `projects.qmd`
2. Add under `## Working Papers & Conference Presentations`:

```markdown
**Paper Title Here**
With Coauthor Name
*Presented at APSA 2025*
```

3. Save and run the workflow

---

### Update Your Bio
1. Open `index.qmd`
2. Edit the text between `:::{#hero-heading}` and `:::`
3. Save and run the workflow

---

### Update Contact Info
1. Open `contact.qmd`
2. Edit as needed
3. Save and run the workflow

---

### Update Your Headshot
1. Save new photo as `headshot.jpeg`
2. Copy to `images/headshot.jpeg` (replace old one)
3. Run the workflow

---

## Preview Before Publishing

To see changes locally before pushing:

```bash
cd /Users/alexanderross/Desktop/website
quarto preview
```

Opens at http://localhost:4000 (or similar). Press Ctrl+C to stop.

---

## Quick Reference

| File | What It Controls |
|------|------------------|
| `index.qmd` | Homepage, bio, education |
| `projects.qmd` | Publications & research |
| `cv.qmd` | CV page (embeds PDF) |
| `contact.qmd` | Contact info |
| `files/Alex_CV.pdf` | Your CV PDF |
| `images/headshot.jpeg` | Your photo |
| `_quarto.yml` | Nav bar, site title, footer |
| `custom.scss` | Colors, fonts, styling |

---

## If Something Goes Wrong

```bash
# See what changed
git status

# Undo all uncommitted changes
git checkout .

# See recent commits
git log --oneline -5
```

---

## Useful Links

- **Your site:** https://alexrosspolisci.com
- **GitHub repo:** https://github.com/aross005/alexrosspolisci.github.io
- **GitHub Pages settings:** https://github.com/aross005/alexrosspolisci.github.io/settings/pages
- **Quarto docs:** https://quarto.org/docs/websites/
