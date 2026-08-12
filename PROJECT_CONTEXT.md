# Project Context: Academic Website for Alexander Ross

## Overview
Personal academic website built with Quarto, deployed to GitHub Pages.

## Status: LIVE (updated June 2026)

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
├── teaching.qmd         # Teaching experience (own navbar tab)
├── contact.qmd          # Contact info
├── custom.scss          # Theme styling (typography, layout - no color overrides)
├── custom.css           # Additional CSS
├── website_helpers.Rmd  # R helper functions for updating site (local only, not in repo)
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
- **Theme:** Solar (Bootswatch dark theme)
- **Unlisted resume:** alexrosspolisci.com/resume.html (not linked, has noindex)

---

## Current Site Content
- **Bio:** Currently on the job market. PhD from UC Riverside 2024 (dissertation on politics of student loan debt). Most recently postdoctoral researcher at Université Laval (ended March 2026), working on PASI immigrant integration study. MPP from UC Riverside School of Public Policy. Bio also mentions naturalistic data research (Yelp/Google Reviews). AmeriCorps alum (South-Central LA), taught English in Beijing. News section commented out (infrastructure kept).
- **Research interests:**
  - Personal debt and political behavior (American)
  - Immigration and immigrant political attitudes (American and comparative)
  - Political behavior (comparative)
  - Inequality
  - Online political behavior
  - Text as data, social media data, and survey methodology
- **Publication:** "Strategic Considerations and Support for Direct Democracy" in *Electoral Studies*
- **Under review:** 4 papers (Deserving Debtors, Buying Love? How Government Benefits Shape Immigrant Political Attachment, Group Threat & Solidarity/Yelp, Home Sweet Home/FREI)
- **Current projects:** Naturalistic data and political attitudes (Yelp/Google Reviews), PASI (immigrant integration panel study, data from Université Laval postdoc)
- **Working papers:** 7 papers listed, including BLM Protests and Online Reviews of Black-Owned Businesses (with Hobbs, Onursal, and Garnett), In the Line of Fire (gun retailers/mass shootings, with Oklobdzija), and Rating the Reckoning (#MeToo/Kavanaugh, women-led businesses)
- **Teaching:** Separate page; 4 courses as instructor of record, TA for Political Science and Public Policy at UC Riverside
- **Grants:** 3 from UC Riverside + CSDC Conference Travel Grant (2025)

---

## What to Edit for Common Updates

| Task | File to Edit |
|------|--------------|
| Update bio/intro | `index.qmd` |
| Update CV | Replace `files/Alex_CV.pdf` |
| Update resume | Replace `files/Alex_Ross_Resume.pdf` |
| Add publication/paper | `projects.qmd` |
| Update teaching info | `teaching.qmd` |
| Update contact info | `contact.qmd` |
| Change site styling | `custom.scss` or `custom.css` |
| Change nav/footer | `_quarto.yml` |
| Change theme | `_quarto.yml` (format > html > theme) - avoid color overrides in custom.scss |

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

**Note:** `_quarto.yml` has a render list that only includes the main site pages (index, cv, resume, projects, teaching, contact). The Projects folder is excluded from rendering.

See `CHEAT_SHEET.md` for detailed instructions.

---

## R Helper Functions

The `website_helpers.Rmd` file contains R functions for updating the site. Open it in RStudio and run the setup chunk to load the functions.

| Function | Purpose |
|----------|---------|
| `update_cv(path)` | Copy new CV PDF to website |
| `update_resume(path)` | Copy new resume PDF to website |
| `render_site()` | Render Quarto site to HTML |
| `preview_site()` | Open local preview in browser |
| `open_live_site()` | Open live site in browser |
| `git_status()` | Show git status |
| `push_changes(message)` | Commit and push to GitHub |
| `quick_cv_update(path)` | All-in-one CV update |

**Quick CV update from R:**
```r
quick_cv_update("~/Downloads/My_New_CV.pdf")
```

---

## Contact Info (for reference)
- Email (preferred): alex.frederick.ross@gmail.com
- Université Laval: alexander-frederick.ross.1@ulaval.ca
- Twitter: @aross005
- GitHub: aross005
- Google Scholar: https://scholar.google.com/citations?user=n7m5UVcAAAAJ&hl=en
