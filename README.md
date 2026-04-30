# 📚 AP Study Hub

<div align="center">

**A sleek, zero-dependency static web app for hosting beautifully rendered AP exam study guides.**

[![Made with HTML](https://img.shields.io/badge/Made%20with-HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![Styled with Tailwind](https://img.shields.io/badge/Styled%20with-Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Math via KaTeX](https://img.shields.io/badge/Math-KaTeX-4B5563?style=flat-square)](https://katex.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Deploy to GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-181717?style=flat-square&logo=github)](https://pages.github.com)

[Live Demo](#) · [Report a Bug](issues) · [Request a Feature](issues)

</div>

---

## ✨ Overview

AP Study Hub is a **single-file SPA** (`index.html`) that dynamically fetches and renders Markdown study guides from a `/guides/` directory. It's purpose-built for AP exam prep, with first-class support for LaTeX math equations, Java/Python code highlighting, and a premium reading experience that mimics a real textbook.

No build tools. No frameworks. No bundlers. Just drop your `.md` files in and go.

---

## 🖼️ Features

| Feature | Details |
|---|---|
| 📄 **Markdown Rendering** | Full GFM support via Marked.js — tables, blockquotes, task lists, and more |
| 🧮 **LaTeX Math** | Inline `$...$` and block `$$...$$` math via KaTeX with a bullet-proof protect→parse→restore pipeline |
| 💻 **Syntax Highlighting** | Java, Python, Bash via Prism.js with language badge labels |
| 🌗 **Dark / Light Mode** | Deep charcoal dark theme + crisp light theme, persisted to `localStorage` |
| 📱 **Fully Responsive** | Mobile-first: single column → 2-col → 3-col grid |
| ⚡ **Zero Build Step** | Pure HTML + CDN libraries, deployable anywhere static files are served |
| 🎨 **Glassmorphism UI** | Per-subject accent colors, noise texture overlay, animated card grid |
| 📖 **Reading Progress Bar** | Fixed top bar tracks scroll position inside the guide viewer |
| 🚫 **Graceful 404** | Elegant in-UI error when a guide file is missing |
| 🔤 **Editorial Typography** | `DM Serif Display` for headings · `Lora` serif for body · `Syne` for UI chrome |

---

## 📁 File Structure

```
ap-study-hub/
├── index.html          ← The entire application (single file)
└── guides/
    ├── calc-bc.md
    ├── chem.md
    ├── csa.md
    ├── eng-lang.md
    ├── eng-lit.md
    ├── physics-c-em.md
    └── physics-c-mech.md
```

That's it. The app discovers guides based on the card definitions in `index.html` — no manifest, no config file needed.

---

## 🚀 Deployment

### Option 1 — GitHub Pages (Recommended)

1. **Fork or clone** this repository.
2. Add your `.md` files to the `/guides/` folder.
3. Go to your repo → **Settings → Pages**.
4. Set source to `main` branch, root `/`.
5. Click **Save**. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

> **Important:** GitHub Pages serves files over HTTP, so `fetch()` calls to `/guides/*.md` work natively. No CORS configuration required.

### Option 2 — Netlify / Vercel

1. Connect your repo to [Netlify](https://netlify.com) or [Vercel](https://vercel.com).
2. Set the **publish directory** to `/` (repo root).
3. No build command needed — leave it blank.
4. Deploy.

### Option 3 — Local Development

Because the app uses `fetch()` to load `.md` files, you need a local server (browsers block file:// fetches by default).

```bash
# Python 3
python -m http.server 8080

# Node.js (npx)
npx serve .

# VS Code
# Install the "Live Server" extension and click "Go Live"
```

Then open `http://localhost:8080` in your browser.

---

## ✍️ Adding or Editing Guides

### Step 1 — Create your Markdown file

Add a `.md` file to the `/guides/` directory:

```
guides/your-subject.md
```

### Step 2 — Register the guide in `index.html`

Open `index.html` and find the `GUIDES` array near the top of the `<script>` block. Add a new entry:

```js
{
  id:    'your-subject',        // Unique slug (matches filename without .md)
  file:  'guides/your-subject.md',
  title: 'AP Your Subject',     // Full display name
  short: 'Your Subject',        // Short label
  tag:   'Science',             // Category tag shown on card
  icon:  'atom',                // Any Lucide icon name → lucide.dev/icons
  desc:  'A short description shown on the home card.',
  color: '#4a7c59',             // Hex accent color for this subject
},
```

Save the file. The new card appears automatically on the homepage.

### Supported Lucide Icons

Browse the full icon set at **[lucide.dev/icons](https://lucide.dev/icons)**. Use the exact icon name (kebab-case) in the `icon` field.

---

## 🧮 Writing LaTeX in Your Guides

The app uses a **protect → parse → restore** pipeline so Marked.js never corrupts your math. Write LaTeX exactly as you would in any LaTeX editor.

### Inline Math
Wrap with single dollar signs. No spaces next to the `$`.

```markdown
The quadratic formula is $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$.
```

### Display / Block Math
Wrap with double dollar signs on their own lines.

```markdown
$$
\oint_C \vec{E} \cdot d\vec{l} = -\frac{d\Phi_B}{dt}
$$
```

### Common Gotchas

| Problem | Fix |
|---|---|
| Underscore inside math breaks italics | Already handled by the pipeline — write `_` freely inside `$...$` |
| Backslash gets eaten | Already handled — `\\`, `\frac`, etc. work correctly |
| Multi-line `align` environment | Use `$$` block delimiters; `\begin{align}` works inside |

---

## 💻 Code Blocks

Specify the language after the opening fence for syntax highlighting:

````markdown
```java
public class Solution {
    public static int binarySearch(int[] arr, int target) {
        int lo = 0, hi = arr.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) lo = mid + 1;
            else hi = mid - 1;
        }
        return -1;
    }
}
```
````

**Supported languages:** `java`, `python`, `bash`, `javascript`, `css`, `html`, `plaintext`

To add more languages, include additional Prism component scripts in `index.html`:

```html
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-c.min.js"></script>
```

---

## 🎨 Customization

### Changing the Color Scheme

All colors are driven by CSS custom properties defined in the `<style>` block:

```css
.light {
  --accent: #c9622f;   /* Change this to your brand color */
  --bg: #f7f6f3;
  /* ... */
}
.dark {
  --accent: #e07a49;
  --bg: #0f0f0f;
  /* ... */
}
```

### Changing Fonts

Replace the Google Fonts `<link>` and the `fontFamily` entries in `tailwind.config`:

```js
theme: {
  extend: {
    fontFamily: {
      sans:    ['Your UI Font', 'sans-serif'],
      serif:   ['Your Body Font', 'serif'],
      display: ['Your Display Font', 'serif'],
    },
  }
}
```

### Adjusting the Grid Layout

The card grid uses Tailwind's responsive grid classes. Edit this line in `index.html`:

```html
<div id="card-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
```

Change `lg:grid-cols-3` to `lg:grid-cols-4` for a 4-column layout on wide screens, etc.

---

## 🛠️ Tech Stack

| Library | Version | Purpose |
|---|---|---|
| [Tailwind CSS](https://tailwindcss.com) | CDN (v3) | Utility-first styling & responsive layout |
| [Marked.js](https://marked.js.org) | 9.1.6 | Markdown → HTML parsing |
| [KaTeX](https://katex.org) | 0.16.9 | Fast LaTeX math rendering |
| [Prism.js](https://prismjs.com) | 1.29.0 | Syntax highlighting |
| [Lucide Icons](https://lucide.dev) | Latest | SVG icon set |
| [Google Fonts](https://fonts.google.com) | — | DM Serif Display · Lora · Syne |

All libraries are loaded via CDN — no `npm install` ever needed.

---

## 🔧 How the LaTeX Pipeline Works

Most Markdown + KaTeX integrations break because Marked.js processes `_`, `*`, and `\` before KaTeX sees them, destroying the math.

AP Study Hub solves this with a three-step pipeline:

```
1. PROTECT  — Extract all $...$ and $$...$$ blocks, replace with safe placeholders
                e.g.  $x^2$  →  INLINEMATH0ENDINLINEMATH

2. PARSE    — Run Marked.js on the placeholder-safe Markdown
                (Marked never touches the math)

3. RESTORE  — Replace placeholders with <span data-math="..."> elements,
              then call katex.render() on each one
```

This approach is robust against all edge cases: multi-line display math, math inside tables, math inside blockquotes, and nested delimiters.

---

## 📋 Subjects Included

| Subject | File | Topics Covered |
|---|---|---|
| AP Calculus BC | `calc-bc.md` | Series, integrals, polar, parametric |
| AP Chemistry | `chem.md` | Thermodynamics, equilibrium, kinetics |
| AP Computer Science A | `csa.md` | Java, OOP, arrays, recursion |
| AP English Language | `eng-lang.md` | Rhetoric, argument, synthesis |
| AP English Literature | `eng-lit.md` | Analysis, poetry, prose, drama |
| AP Physics C: E&M | `physics-c-em.md` | Electrostatics, circuits, magnetism |
| AP Physics C: Mechanics | `physics-c-mech.md` | Kinematics, rotation, oscillations |

---

## 🐛 Troubleshooting

**Guide shows raw Markdown / symbols not rendering**
Make sure you're serving the site via a local server, not opening `index.html` directly as a `file://` URL. `fetch()` is blocked by browsers in `file://` context.

**Math renders as raw `$...$` text**
Check that there are no spaces immediately inside your dollar signs: `$ x^2 $` will not render — use `$x^2$`.

**404 error in the UI even though the file exists**
Verify the filename in the `GUIDES` array exactly matches the file on disk (case-sensitive on Linux/macOS). Check that the file is committed and pushed to your repo.

**Code block not highlighted**
Confirm the language name after the triple backtick matches a loaded Prism component. Add the corresponding component `<script>` tag if it's missing.

**Dark mode resets on reload**
The theme is stored in `localStorage` under the key `ap-theme`. If your browser blocks localStorage, the theme will default to your OS preference on each load.

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

For major changes, please open an issue first to discuss what you'd like to change.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

You are free to use, copy, modify, merge, publish, distribute, and sublicense this software for any purpose, including commercial use, with attribution.

---

<div align="center">

Built with ♥ for AP students everywhere.

*Good luck on your exams.*

</div>
