# 🧬 BSB511 / BENG451 — Interactive Bioinformatics Widgets

Interactive learning tools for the Bioinformatics Fundamentals course (2025–2026 Spring Semester).

## Widgets

| Widget | Description |
|--------|-------------|
| [DNA Sequence Explorer](dna-explorer.html) | Central dogma: transcription, translation, 6-frame reading |
| [Pairwise Alignment Sandbox](alignment-sandbox.html) | Needleman-Wunsch & Smith-Waterman DP matrix practice |
| [Phylogenetic Tree Interpreter](phylo-interpreter.html) | UPGMA & Neighbor-Joining step-by-step tree building |
| [Sequence Motif Finder](motif-finder.html) | PROSITE pattern scanning on protein & DNA sequences |

## How It Works

Each widget is a **self-contained HTML file**. No build step, no npm, no Node.js needed. They load React from a CDN and run entirely in the browser. Just open any `.html` file directly.

---

## Deployment

### Option A: GitHub Pages (recommended — free, automatic)

1. Create a new GitHub repository (e.g., `bioinfo-widgets`)

2. Push this folder to the repo:
   ```bash
   cd site
   git init
   git add .
   git commit -m "Initial commit: bioinformatics widgets"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/bioinfo-widgets.git
   git push -u origin main
   ```

3. Enable GitHub Pages:
   - Go to **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main** / root
   - Click **Save**

4. Your site will be live at:
   ```
   https://YOUR_USERNAME.github.io/bioinfo-widgets/
   ```

That's it. Every time you push changes, the site updates automatically.

### Option B: Your own web server

Just copy the entire folder to your web server's document root:

```bash
scp -r site/* user@yourserver:/var/www/html/bioinfo-widgets/
```

Or if you prefer a subdirectory under an existing site:

```bash
scp -r site/* user@yourserver:/var/www/html/course/widgets/
```

No server-side processing is needed — these are pure static HTML files.

### Option C: Open locally

Double-click any `.html` file. They work offline (after the first load caches the CDN scripts).

---

## Embedding in Other Pages

### In a Notion page, LMS, or course website (iframe)

```html
<iframe
  src="https://YOUR_USERNAME.github.io/bioinfo-widgets/dna-explorer.html"
  width="100%" height="800" frameborder="0">
</iframe>
```

### In MS Teams

Share the GitHub Pages link directly in a Teams channel. Students click and it opens in their browser.

### In JupyterHub (TLJH)

Add a Markdown cell in any Jupyter notebook:

```markdown
**Interactive Widget:** [Open DNA Sequence Explorer](https://YOUR_USERNAME.github.io/bioinfo-widgets/dna-explorer.html)
```

Or embed inline with an IFrame display:

```python
from IPython.display import IFrame
IFrame('https://YOUR_USERNAME.github.io/bioinfo-widgets/dna-explorer.html', width=900, height=700)
```

---

## Customization

Each HTML file is self-contained. To modify a widget:

1. Open the `.html` file in any text editor
2. The React/JSX code is inside the `<script type="text/babel">` tag
3. Edit directly — Babel compiles it in the browser
4. Save and refresh

To add a new widget to the landing page, edit `index.html` and add a new card in the `.grid` div.

---

## File Structure

```
site/
├── index.html                  # Landing page with links to all widgets
├── dna-explorer.html           # Central dogma widget
├── alignment-sandbox.html      # Pairwise alignment widget
├── phylo-interpreter.html      # Phylogenetic tree widget
└── motif-finder.html           # Sequence motif widget
```

---

## License

Educational use. Created for BSB511 / BENG451 — Bioinformatics Fundamentals.
