# Alexander Ross - Academic Website

A personal academic website built with [Quarto](https://quarto.org/).

## Quick Start

### Prerequisites
- [Quarto](https://quarto.org/docs/get-started/) (already installed)
- [RStudio](https://posit.co/download/rstudio-desktop/) (recommended)
- Git and a GitHub account

### Local Development

1. **Open in RStudio**: Open the `website` folder as an RStudio project

2. **Preview the site**:
   ```bash
   quarto preview
   ```
   This opens a live preview at http://localhost:4000

3. **Edit content**: Modify the `.qmd` files:
   - `index.qmd` - Homepage/bio
   - `cv.qmd` - Your CV
   - `projects.qmd` - Research projects
   - `contact.qmd` - Contact information

4. **Add your headshot**: Replace `images/headshot.jpg` with your professional photo

5. **Render the site**:
   ```bash
   quarto render
   ```
   Output goes to the `docs/` folder

---

## Deploy to GitHub Pages

### Step 1: Create GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Create a repository named `alexrosspolisci.github.io` (or any name)
3. Make it **Public**
4. Don't initialize with README (we have files already)

### Step 2: Push to GitHub

```bash
cd /Users/alexanderross/Desktop/website

# Initialize git
git init
git add .
git commit -m "Initial commit: Quarto academic website"

# Add remote and push (replace with your username)
git remote add origin https://github.com/YOUR_USERNAME/alexrosspolisci.github.io.git
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Source", select **Deploy from a branch**
4. Select **main** branch and **/docs** folder
5. Click **Save**

Your site will be live at: `https://YOUR_USERNAME.github.io/alexrosspolisci.github.io/`

---

## Connect Your Custom Domain (alexrosspolisci.com)

### Step 1: Add Domain to GitHub

1. In your repo: **Settings** → **Pages** → **Custom domain**
2. Enter: `alexrosspolisci.com`
3. Click **Save**
4. Check "Enforce HTTPS" (after DNS propagates)

### Step 2: Update DNS at Your Domain Registrar

Log into wherever you registered `alexrosspolisci.com` (GoDaddy, Namecheap, Google Domains, etc.)

**Option A: CNAME Record (Recommended)**
- Type: CNAME
- Host/Name: `www`
- Value: `YOUR_USERNAME.github.io`
- TTL: 3600 (or default)

For apex domain (no www), add A records:
- Type: A
- Host/Name: `@`
- Value: `185.199.108.153`
- Value: `185.199.109.153`
- Value: `185.199.110.153`
- Value: `185.199.111.153`

### Step 3: Create CNAME File

Add a file named `CNAME` (no extension) to your repo root with:
```
alexrosspolisci.com
```

### Step 4: Wait for DNS Propagation

DNS changes can take 24-48 hours to fully propagate. You can check status at:
- [dnschecker.org](https://dnschecker.org/)

---

## Updating Your Site

After making changes:

```bash
# Render the site
quarto render

# Commit and push
git add .
git commit -m "Update: description of changes"
git push
```

GitHub Pages will automatically deploy the updated `docs/` folder.

---

## Customization

### Change Theme
Edit `_quarto.yml` and change the theme. Options include:
- `cosmo` (current)
- `flatly`
- `lumen`
- `minty`
- `sandstone`

See all themes: https://quarto.org/docs/output-formats/html-themes.html

### Change Colors
Edit `custom.scss` to modify:
- `$primary` - Main accent color
- `$link-color` - Link color
- `$body-bg` - Background color

### Add a Blog
1. Create a `posts/` folder
2. Add `blog.qmd` with listing configuration
3. Add posts as `.qmd` files in `posts/`

See: https://quarto.org/docs/websites/website-blog.html

---

## File Structure

```
website/
├── _quarto.yml      # Site configuration
├── index.qmd        # Homepage
├── cv.qmd           # CV page
├── projects.qmd     # Research page
├── contact.qmd      # Contact page
├── custom.scss      # Theme customization
├── custom.css       # Additional styles
├── images/
│   └── headshot.jpg # Your photo
└── docs/            # Rendered site (auto-generated)
```

---

## Resources

- [Quarto Documentation](https://quarto.org/docs/websites/)
- [Quarto Gallery](https://quarto.org/docs/gallery/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
