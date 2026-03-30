# Setting up your Jekyll blog on GitHub Pages
## Complete guide for Preethi's geospatial portfolio

---

## WHAT YOU'RE UPLOADING

Upload ALL of these to your GitHub repo (preethimb.github.io):

```
your repo/
├── index.html           ← your existing portfolio page (already there)
├── resume.pdf           ← your resume PDF
├── _config.yml          ← Jekyll settings ← NEW
├── Gemfile              ← tells GitHub which Jekyll version ← NEW
├── blog/
│   └── index.html       ← your blog listing page ← NEW
├── _layouts/
│   ├── default.html     ← site wrapper with nav/footer ← NEW
│   └── post.html        ← individual post layout ← NEW
├── _posts/
│   ├── 2024-03-15-mapping-urban-heat-islands.md   ← example post ← NEW
│   └── 2024-01-20-getting-started-google-earth-engine.md ← NEW
└── assets/
    └── images/
        └── (your cover images and post photos go here)
```

---

## STEP 1 — Upload the files to GitHub

1. Go to github.com → your repo (preethimb.github.io)
2. Click **"Add file" → "Upload files"**
3. Drag ALL the new files/folders above onto the page
4. Click **"Commit changes"**
5. Wait ~2 minutes → visit preethimb.github.io/blog/ ✓

---

## STEP 2 — Write your first real blog post

Post files live in the `_posts/` folder. Each file MUST be named:
```
YYYY-MM-DD-your-post-title-with-dashes.md
```

Copy this template and fill it in:

```markdown
---
layout: post
title: "Your Post Title Here"
date: 2024-06-01
tags: [GIS]                        # one tag shown as a label
cover_image: my-cover-photo.jpg    # optional — put image in assets/images/
read_time: 5                       # estimated reading time in minutes
location: Bangalore, India         # optional
excerpt: >
  A 1–2 sentence summary that shows on the blog listing card.
  Keep it punchy.
---

Your first paragraph goes here. This is what readers see before the "Read more" break.

<!--more-->

Everything after this line is hidden on the listing page, shown on the full post.

## A heading

Your content here. You can use:
- **bold text**
- *italic text*
- [links](https://example.com)
- ![images]({{ site.baseurl }}/assets/images/your-photo.jpg)
```

---

## STEP 3 — Move your Medium articles over

For each Medium article:

1. **Copy the text** from Medium (Ctrl+A, Ctrl+C on the article page)
2. **Create a new .md file** in `_posts/` with the correct date-based name
3. **Paste and clean up** — headings become `##`, bold becomes `**word**`
4. **Add the front matter** at the top (the `---` section with title, date, tags)
5. **Upload images separately** to `assets/images/` and reference them in the post

---

## STEP 4 — Embed maps in posts

### Option A: Google MyMaps (easiest)
1. Go to mymaps.google.com
2. Create or import your map
3. Click Share → Embed on my site → copy the `<iframe>` code
4. Paste it inside a `<div class="map-embed">` in your post:

```html
<div class="map-embed">
  <iframe src="YOUR_GOOGLE_MAPS_EMBED_URL" allowfullscreen loading="lazy"></iframe>
</div>
```

### Option B: Felt.com (better for GIS layers)
1. Upload your GeoJSON/shapefile to felt.com
2. Style it → Share → Embed
3. Same `<div class="map-embed">` wrapper

### Option C: QGIS2Web (fully self-hosted)
1. In QGIS: Plugins → qgis2web → Export as Leaflet
2. Upload the exported folder to `assets/maps/my-map-name/`
3. Embed with:
```html
<div class="map-embed">
  <iframe src="{{ site.baseurl }}/assets/maps/my-map-name/index.html"></iframe>
</div>
```

---

## STEP 5 — Add images to posts

1. Put image files in `assets/images/` in your repo
2. Reference in Markdown: `![Caption]({{ site.baseurl }}/assets/images/filename.jpg)`
3. For a caption: use a figure block:

```markdown
<figure>
  <img src="{{ site.baseurl }}/assets/images/filename.jpg" alt="Description"/>
  <figcaption>Your caption here.</figcaption>
</figure>
```

---

## QUICK REFERENCE — Markdown cheatsheet

| What you want | What to type |
|---|---|
| Big heading | `## Heading` |
| Smaller heading | `### Heading` |
| Bold | `**bold text**` |
| Italic | `*italic text*` |
| Link | `[link text](https://url.com)` |
| Image | `![alt text]({{ site.baseurl }}/assets/images/file.jpg)` |
| Blockquote | `> Your quote here` |
| Code (inline) | `` `code` `` |
| Code block | ` ```python ` then code then ` ``` ` |
| Horizontal rule | `---` |

---

## TROUBLESHOOTING

**Blog page not loading?**
→ Make sure `_config.yml` is in the ROOT of your repo (not inside a folder)

**Post not appearing?**
→ Check the filename format: must be `YYYY-MM-DD-title.md`
→ Check the date in the front matter isn't in the future

**Images not showing?**
→ Filename is case-sensitive — `Photo.jpg` ≠ `photo.jpg`
→ Make sure the file is in `assets/images/`

**Map embed showing blank?**
→ Google Maps embeds require an API key for some uses — try Felt.com instead

---

Questions? Paste any error message here and I'll help fix it!
