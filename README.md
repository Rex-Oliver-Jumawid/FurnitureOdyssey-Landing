# Furniture Odyssey landing page

Standalone marketing site for Furniture Odyssey. This is intentionally separate from the authenticated Furniture Odyssey POS product. It uses plain HTML, CSS and JavaScript and does not require Node.js, npm, Next.js, an API, or database credentials.

## Project layout

```text
furniture-odyssey-landing/
├── index.html                              # Full landing page, including 2-second module preview
├── assets/
│   ├── images/
│   │   ├── brand-mark.png                  # New supplied Furniture Odyssey logo, header and site icons
│   │   ├── demo-poster.webp               # Real frame from the demo
│   └── videos/
│       └── furniture-odyssey-demo.mp4     # Optimized H.264/AAC, 1280 × 720
├── README.md
└── .gitignore
```

The 2-minute-36-second video was encoded from the supplied `demo.mov` (approximately 45 MB) into an approximately 5.6 MB MP4. The HTML intentionally does not autoplay the long video. It has an image poster, native accessible video controls, and a click-to-play button. No third-party player, runtime, or API key is used.

## Preview locally

Run this from the project root:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000/` in your browser. Stop the server with Ctrl+C. HTML will also open from disk, but a local web server more closely matches production asset behavior.

## Deploy to Vercel (recommended: Git integration)

1. Create a dedicated GitHub repository for this marketing site, such as `FurnitureOdyssey-Landing`, and commit this **entire directory** to the repository root. Keep the assets folder in Git with the HTML.
2. In [Vercel](https://vercel.com/new), choose **Add New Project** and import the new repository.
3. Select **Framework Preset: Other**. Use the repository root as the **Root Directory**. Do not add a build command. Leave the **Output Directory** at the root (the directory containing `index.html`), rather than `public` or `dist`.
4. Deploy. Vercel serves `index.html` from `/`, and the media from `/assets/...`.
5. Add your custom marketing domain in Vercel's project **Settings > Domains**, if desired.

The footer consultation CTA uses the official Cal.com popup embed for `https://cal.com/rex-oliver-jumawid-mmz8ct/furniture-odyssey-consultation`. If the embed script cannot load, the same CTA remains a normal link to the public booking page in a new tab. Configure consultation questions, availability, video provider, and calendar connections in Cal.com, not in this HTML. No Cal.com API key is needed.

The POS link is independent: `https://furniture-odyssey-pos.vercel.app/demo`. It opens in a new tab. Updating the marketing site won't redeploy or alter the product's database, authentication, or business operations.

### CLI alternative

From this folder after signing into your Vercel account:

```bash
npx vercel
npx vercel --prod
```

When prompted, choose **Other** (no framework), project root, and no build step. Git integration is preferred for automatic deployments and preview URLs with every commit.

## Updating images or videos

- Store website images and posters in `assets/images/`.
- Store optimized MP4 or WebM video assets in `assets/videos/`.
- Use relative URLs such as `assets/images/example.webp` inside `index.html`.
- Keep large original edit files (`.mov`, raw recordings) outside the deployed folder. Only commit the optimized publication assets.
- For future videos that are substantially larger, high-traffic, or require adaptive streaming, use a video service such as Cloudflare Stream, Mux, or Vercel Blob instead of putting every large video in Git.

## Smoke checks before releasing

- Check the product demo video plays with audio and can be paused/scrubbed.
- Review at a desktop and mobile width, and ensure no horizontal overflow.
- Verify the rotating hero preview advances every two seconds and manual navigation works.
- Confirm pricing and package amounts: the post-launch package total is ₱24,999; the launch offer is ₱11,999.
- Check links to the live demo, the Cal.com consultation booking popup and its link fallback, and other calls to action. Test a real booking on the production site, including timezone, confirmation, and calendar delivery.
- Test the production deployment's root URL and the `/assets/videos/furniture-odyssey-demo.mp4` URL after pushing.

The landing page navbar, favicon, and Apple touch icon all use the current supplied `assets/images/brand-mark.png`. Legacy brand icon assets were removed.
