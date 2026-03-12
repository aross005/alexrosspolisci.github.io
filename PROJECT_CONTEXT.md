# Project Context: Academic Website for Alexander Ross

## Overview
Personal academic website built with Quarto, deployed to GitHub Pages.

## Status: COMPLETE AND LIVE

**Live URL:** https://alexrosspolisci.com

---

## Completed Setup
- [x] Quarto website built
- [x] Content migrated from WordPress
- [x] Headshot and CV PDF added
- [x] Pushed to GitHub: https://github.com/aross005/alexrosspolisci.github.io
- [x] GitHub Pages enabled (main branch, /docs folder)
- [x] Custom domain connected (DNS via WordPress.com)
- [x] HTTPS enabled

---

## File Structure
```
/Users/alexanderross/Desktop/website/
├── _quarto.yml          # Site config (nav, theme, footer, render list)
├── index.qmd            # Homepage with bio
├── cv.qmd               # Embeds CV PDF (academic)
├── resume.qmd           # Embeds resume PDF (unlisted, noindex)
├── projects.qmd         # Research & publications
├── contact.qmd          # Contact info
├── custom.scss          # Theme styling (colors, navbar, sections)
├── custom.css           # Additional CSS
├── images/
│   └── headshot.jpeg    # Professional photo
├── files/
│   ├── Alex_CV.pdf      # Academic CV PDF
│   └── Alex_Ross_Resume.pdf  # Professional resume PDF
├── docs/                # Rendered site (deployed to GitHub Pages)
├── CNAME                # Custom domain file
├── CHEAT_SHEET.md       # Quick reference for updates
└── README.md            # Deployment instructions
```

---

## Key Info
- **GitHub username:** aross005
- **GitHub repo:** alexrosspolisci.github.io
- **Domain registrar:** WordPress.com
- **Live domain:** alexrosspolisci.com
- **Quarto version:** 1.3.450
- **Theme:** Journal (Bootswatch)
- **Unlisted resume:** alexrosspolisci.com/resume.html (not linked, has noindex)

---

## Current Site Content
- **Bio:** Postdoctoral researcher at Université Laval working on PASI immigrant integration study. PhD from UC Riverside 2024 (dissertation on politics of student loan debt). MPP from UC Riverside School of Public Policy. AmeriCorps alum (South-Central LA), taught English in Beijing.
- **Research interests:**
  - Personal debt and political behavior (American)
  - Immigration and immigrant political attitudes (American and comparative)
  - Political behavior (comparative)
  - Inequality
  - Text as data and survey methodology
- **Publication:** "Strategic Considerations and Support for Direct Democracy" in *Electoral Studies*
- **Current project:** PASI (immigrant integration panel study at Université Laval)
- **Working papers:** 8 papers listed with co-authors and conference presentations

---

## What to Edit for Common Updates

| Task | File to Edit |
|------|--------------|
| Update bio/intro | `index.qmd` |
| Update CV | Replace `files/Alex_CV.pdf` |
| Update resume | Replace `files/Alex_Ross_Resume.pdf` |
| Add publication/paper | `projects.qmd` |
| Update contact info | `contact.qmd` |
| Change site styling | `custom.scss` or `custom.css` |
| Change nav/footer | `_quarto.yml` |
| Change theme | `_quarto.yml` (format > html > theme) |

---

## Update Workflow
```bash
cd /Users/alexanderross/Desktop/website
# 1. Edit .qmd files
# 2. Render
quarto render
# 3. Stage, commit, push
git add .
git commit -m "Description of changes"
git push
```

**Note:** `_quarto.yml` has a render list that only includes the main site pages (index, cv, resume, projects, contact). The Projects folder is excluded from rendering.

See `CHEAT_SHEET.md` for detailed instructions.

---

## Contact Info (for reference)
- Email (preferred): alex.frederick.ross@gmail.com
- Université Laval: alexander-frederick.ross.1@ulaval.ca
- Twitter: @aross005
- GitHub: aross005
- Google Scholar: https://scholar.google.com/citations?user=n7m5UVcAAAAJ&hl=en
