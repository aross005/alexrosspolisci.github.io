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
├── _quarto.yml          # Site config (nav, theme, footer)
├── index.qmd            # Homepage with bio
├── cv.qmd               # Embeds CV PDF
├── projects.qmd         # Research & publications
├── contact.qmd          # Contact info
├── custom.scss          # Theme styling
├── custom.css           # Additional CSS
├── images/
│   └── headshot.jpeg    # Professional photo
├── files/
│   └── Alex_CV.pdf      # CV PDF
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

---

## Current Site Content
- **Bio:** Postdoctoral researcher at Université Laval, PhD from UC Riverside 2024
- **Research interests:** Personal debt, political behavior, American politics
- **Publication:** "Strategic Considerations and Support for Direct Democracy" in *Electoral Studies*
- **Current project:** PASI (immigrant integration panel study at Université Laval)
- **Working papers:** 8 papers listed with co-authors and conference presentations

---

## What to Edit for Common Updates

| Task | File to Edit |
|------|--------------|
| Update bio/intro | `index.qmd` |
| Update CV | Replace `files/Alex_CV.pdf` |
| Add publication/paper | `projects.qmd` |
| Update contact info | `contact.qmd` |
| Change site styling | `custom.scss` or `custom.css` |
| Change nav/footer | `_quarto.yml` |

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

See `CHEAT_SHEET.md` for detailed instructions.

---

## Contact Info (for reference)
- Email (preferred): alex.frederick.ross@gmail.com
- Université Laval: alexander-frederick.ross.1@ulaval.ca
- Twitter: @aross005
- GitHub: aross005
- Google Scholar: https://scholar.google.com/citations?user=n7m5UVcAAAAJ&hl=en
