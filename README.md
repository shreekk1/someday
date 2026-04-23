# My World — Vlog Site
### Production-Ready Personal Journal — Nepal → New York

---

## 📁 File Structure

```
/
├── index.html          ← Main page (all chapters)
├── 404.html            ← Custom 404 error page
├── privacy.html        ← Privacy policy
├── terms.html          ← Terms of use
├── _headers            ← Security headers (Netlify or Cloudflare Pages)
├── sitemap.xml         ← SEO sitemap (create manually or generate)
├── robots.txt          ← Search engine crawler rules
└── assets/
    ├── IMG_8090.jpeg
    ├── IMG_5749.jpeg
    ├── IMG_4731.jpeg
    ├── IMG_4726.jpeg
    ├── IMG_2441.jpeg
    ├── IMG_3759.gif
    ├── IMG_4474.jpeg
    ├── IMG_4717.jpeg
    ├── IMG_4656.jpeg
    ├── IMG_3519.jpeg
    ├── IMG_7707.jpeg
    └── C2E79B65-3C67-4763-81C0-B8DAB4C4CCE3.jpeg
```

---

## 🚀 Deployment to GitHub Pages

1. Move all your images into an `assets/` folder in your repo root
2. Commit all files: `index.html`, `404.html`, `privacy.html`, `terms.html`, `_headers`
3. Go to your repo → **Settings** → **Pages**
4. Set source: `Deploy from branch` → `main` → `/root`
5. Your site will be live at `https://shreekk1.github.io/Vlog-/`

> **Note:** GitHub Pages doesn't read `_headers`. For real security headers, deploy via **Netlify** (free, drag-and-drop upload) which reads the `_headers` file automatically.

---

## ✏️ Editing Guide

### Change the Site Title
In `index.html`, find:
```html
<title>My World — A Personal Story | Nepal to New York</title>
```
Change the text between `<title>` tags.

Also update:
```html
<meta property="og:title" content="My World — A Personal Story" />
<meta name="twitter:title" content="My World — A Personal Story" />
```

### Change the Hero Text
Find the hero section (search for `id="hero-heading"`):
```html
<h1 class="hero-title" id="hero-heading">
  Living<br><em>Colorfully,</em><br>Loving Deeply
</h1>
<p class="hero-subtitle">From the vibrant streets of Nepal...</p>
```
Edit the `<h1>` and `<p>` text directly.

### Add or Change Photos
All images reference `assets/YOUR_IMAGE.jpeg`. To swap a photo:
1. Add your new image to the `assets/` folder
2. Find the `<img src="assets/OLD_NAME.jpeg"` tag in `index.html`
3. Change it to `<img src="assets/NEW_NAME.jpeg"`
4. Update the `alt` attribute with an accurate description

### Add a New Chapter Section
Copy an existing section block (e.g., `chapter-nature`), paste it before `</main>`, and give it a new `id`:
```html
<section class="chapter-nature" id="my-new-chapter" aria-labelledby="my-heading">
  ...
</section>
```
Then add a nav link:
```html
<li><a href="#my-new-chapter">My Chapter</a></li>
```

### Change Colors
All colors are in CSS variables at the top of the `<style>` block:
```css
:root {
  --cream:      #faf7f2;  /* Page background */
  --terracotta: #c4714a;  /* Section labels, accents */
  --rose:       #d4897a;  /* Hero italic, footer */
  --gold:       #c9a96e;  /* Nav hover, gallery title */
  --sky:        #7fb3d3;  /* NYC chapter accent */
  --deep:       #2a1f1a;  /* Dark backgrounds */
  --soft:       #7a5a4a;  /* Body text on light bg */
}
```

### Update the Footer
Find the `<footer>` section near the bottom. Edit the title, subtitle, and chapter links as needed.

### Update Privacy & Terms
Edit `privacy.html` and `terms.html` directly. Update the "Last updated" date at the top when you make changes.

---

## 🔒 Security Notes

- **No forms or user input** on this site = very low attack surface
- All `<img>` tags use `loading="lazy"` for performance
- All external links should use `rel="noopener noreferrer"`
- CSP headers are set via both `<meta>` tags and `_headers` file
- No credentials, API keys, or secrets anywhere in the codebase
- All JavaScript runs in an IIFE with `'use strict'`

---

## ⚡ Performance Tips

- Compress images before uploading (use [Squoosh](https://squoosh.app/) — free)
- Convert large JPEGs to WebP format for ~30% smaller files
- The hero image (`IMG_8090.jpeg`) loads `eager` — keep it under 300KB
- All other images load `lazy` — they load only when scrolled into view
- Consider adding `width` and `height` attributes to all images to prevent layout shift

---

## 🧪 Testing Checklist Before Launch

- [ ] All images load correctly (no broken image icons)
- [ ] Nav links scroll to correct sections
- [ ] Mobile menu opens and closes on small screens
- [ ] Keyboard navigation works (Tab through nav, Enter on links)
- [ ] Screen reader test: use VoiceOver (Mac) or NVDA (Windows)
- [ ] 404 page appears when visiting a non-existent URL
- [ ] Privacy and Terms pages load
- [ ] Run [PageSpeed Insights](https://pagespeed.web.dev/) — aim for 90+
- [ ] Run [WAVE accessibility checker](https://wave.webaim.org/)

---

*Built with HTML, CSS, and vanilla JavaScript — no build tools, no dependencies.*
