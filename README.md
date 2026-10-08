# Shuffle PDF
### Website Link - https://shuffle-pdf.netlify.app/

A free, privacy-friendly PDF merger and page arranger that runs entirely in the browser. No uploads, no server, no sign-up.

## Features

- Merge multiple PDFs into one
- Convert Word (`.docx`) files and images (JPG, PNG, WebP) to PDF pages
- Drag and drop pages to reorder them (or use the ◀ ▶ buttons on touch devices)
- Rotate or delete individual pages
- Download the result as `merged.pdf`

## How it works

Everything is a single static file, `index.html`. All processing happens on the user's device.

| Task | Library |
|---|---|
| Render page thumbnails | [PDF.js](https://mozilla.github.io/pdf.js/) |
| Merge, rotate and save PDFs | [pdf-lib](https://pdf-lib.js.org/) |
| Word to HTML | [mammoth.js](https://github.com/mwilliamson/mammoth.js) |
| HTML to PDF | [html2pdf.js](https://github.com/eKoopmans/html2pdf.js) |

Libraries are loaded from the cdnjs CDN, so there is nothing to install or build.

## Run locally

1. Download `pdf-merger.html` and rename it to `index.html`.
2. Open it in a browser, or serve the folder:

```bash
npx serve .
# or
python3 -m http.server 8000
```

An internet connection is needed the first time so the CDN scripts can load.

## Deploy

Because it's a static site, any static host works:

- **Cloudflare Pages / Netlify**: drag and drop the folder in the dashboard
- **GitHub Pages**: push `index.html` to a repo, then enable Pages in Settings
- **Vercel**: `npx vercel` from the project folder

To use your own domain, add it in the host's settings and point your DNS records as instructed. HTTPS is set up automatically.

## Limitations

- Word conversion is basic: text, headings, lists, tables and inline images are kept, but exact fonts, headers/footers and complex layouts are not. For high-fidelity conversion, add a backend using LibreOffice.
- Password-protected PDFs may fail to load.
- Very large files are limited by the user's device memory.

## Roadmap ideas

- [ ] Split PDF / extract page ranges
- [ ] Add text, signatures and highlights
- [ ] Compression (needs a backend)
- [ ] Pre-bundle libraries locally for offline use
- [ ] Privacy policy page

## Privacy

Files are processed locally in the browser and are never sent to a server. If you add a backend later, document what is stored and for how long.

## License

MIT. Add a `LICENSE` file before publishing.
