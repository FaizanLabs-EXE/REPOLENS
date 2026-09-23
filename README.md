# RepoLens — GitHub Intelligence

> ╰─➤ ⚡ **𝐁𝐔𝐈𝐋𝐓 𝐁𝐘 𝐅𝐀𝐈𝐙𝐀𝐍™**

RepoLens is a lightweight, responsive Progressive Web App for discovering GitHub repositories by intent, inspecting explainable project-health signals, comparing candidates, saving discoveries locally, and exporting search data.

## Why this concept?

GitHub search is powerful but raw. RepoLens adds a decision workspace around it:

- **Intent-first search** — describe a problem instead of knowing exact repository names.
- **Health signal** — a transparent 0–100 heuristic based on activity, license, archive state, stars/forks and issues.
- **Compare Lab** — compare up to four repositories side-by-side.
- **Trending Radar** — automated scans across AI agents, developer tools, automation, self-hosting and observability.
- **Local library** — saved repositories are stored in browser localStorage.
- **Export** — export the current result set as JSON.
- **PWA** — installable on Android, Windows, macOS and Linux browsers.
- **Responsive GUI** — desktop sidebar automatically becomes a compact mobile navigation.
- **Offline shell** — UI assets are cached by the service worker; GitHub data requires internet.

## Run locally

No Node/npm is required.

### Option A — Python
```bash
python -m http.server 8080
```
Then open `http://localhost:8080`.

### Option B — VS Code
Install **Live Server**, then open `index.html` with Live Server.

> Do not open `index.html` directly as `file://...` if you want the service worker/PWA features.

## GitHub token

A token is optional. Without one, GitHub's unauthenticated API rate limit applies. If the limit is reached, add a GitHub personal access token through **GitHub Token**. RepoLens stores the token only in the current browser's localStorage and sends it only to `api.github.com`.

For production deployments, a server-side proxy is preferable to browser-stored credentials.

## Architecture

```text
index.html
  ├── styles.css        Responsive UI + animation
  ├── app.js            GitHub API + scoring + compare/save/export
  ├── sw.js             PWA cache
  ├── manifest.webmanifest
  └── assets/icon.svg
```

The project intentionally uses plain HTML/CSS/JavaScript so it can be hosted as a static GitHub Pages site with no build pipeline.

## Health signal

The score is **not a security audit or recommendation**. It is an explainable heuristic:

- description, license and homepage presence
- archive/disabled penalties
- stars/forks activity signals
- open issue count
- recent update recency

Always inspect a repository's source, license, maintainers, releases and issue history before relying on it.

## GitHub Pages

1. Create a repository.
2. Upload all files preserving the folder structure.
3. Go to **Settings → Pages**.
4. Choose **Deploy from a branch**.
5. Select `main` and `/ (root)`.
6. Save.

## License

MIT. See `LICENSE`.
