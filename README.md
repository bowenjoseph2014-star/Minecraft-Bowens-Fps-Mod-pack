# Bowens FPS Mod Pack — Website

This repository contains a simple webpage (index.html) that provides a "Download Now" button to download the Bowens FPS Mod Pack ZIP file from a Discord CDN URL.

## 🎮 Join Our Server

Want to play with us? Join the Bowens FPS server!

| Edition  | Address |
|----------|---------|
| **Java** | `slugpve.minekeep.gg` |
| **Bedrock** | `slugpve.bedrock.minekeep.gg` |

## Files

- `index.html` — A single-page site with a button that attempts a programmatic download (fetch -> blob -> save). If that fails (CORS or expired link), it opens the file URL in a new tab so the browser can save it manually.
- `README.md` — This file.

## How it works

- Primary method: the page tries to fetch the ZIP and create a Blob so the browser saves the file with the correct filename.
- Fallback: if the fetch is blocked (CORS) or the token in the Discord URL expired, the page opens the file URL in a new tab for manual saving.

## Notes about the download URL

The current download URL in `index.html` points to a Discord CDN link that includes temporary query parameters. Those tokens can expire and will cause downloads to fail (e.g. 403). For reliable, long-term downloads, consider:

- Upload the ZIP as a GitHub Release asset and update `index.html` to point to the release asset URL.
- Host the ZIP on a stable CDN or object storage (S3, Cloudflare R2, etc.) with proper CORS headers.
- If the file is small enough (<100 MB), you could add it directly to the repository (not recommended for large files or frequently updated assets).

If the URL supports CORS, the current programmatic download approach will save the file automatically; otherwise the fallback will open the link in a new tab.

## Enable GitHub Pages

To publish this page via GitHub Pages:

1. Go to the repository Settings -> Pages.
2. For "Source", select the `main` branch and root (`/`) folder.
3. Save and wait a minute for the site to publish.

When published, the site will be available at:

```
https://bowenjoseph2014-star.github.io/Minecraft-Bowens-Fps-Mod-pack/
```

## Make downloads more reliable (recommended)

- Create a GitHub Release and attach the ZIP file as an asset. Release assets have stable URLs that you can link to from `index.html`.
- Ensure the host sets CORS headers if you want the programmatic fetch-and-save behavior.

## Local testing

You can open `index.html` directly in a browser to test the UI, but the programmatic fetch may be restricted by CORS when running from the file:// protocol. Use a simple local server instead, e.g.:

```bash
# Python 3
python -m http.server 8000
# then visit http://localhost:8000
```

## Want me to do this for you?

I can:

- Create a GitHub Release and upload the ZIP file (you'd need to provide the ZIP or a stable source URL).
- Update `index.html` to point to a different URL (release asset, S3, etc.).

Reply with what you'd like me to do next.
