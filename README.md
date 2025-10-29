# Lushyweb.github.io
# Lushy — Static Site (lushy-site)

This folder contains a complete, responsive, static site called "Lushy". It's pure HTML/CSS/JS and ready to deploy to GitHub Pages.

Contents
- `index.html` — landing page
- `social.html` — about & social links
- `secret.html` — hidden gateway (password or token unlock)
- `dashboard.html` — private dashboard (requires unlocking via `secret.html`)
- `css/style.css` — theme variables and site styles
- `js/departures.js` — live Nottingham departures widget
- `js/dashboard.js` — auth, to-dos, notes, mock analytics
- `assets/` — logos and favicon
- `.github/workflows/deploy.yml` — GitHub Actions workflow to deploy `lushy-site/` to GitHub Pages

Quick start
1. Put this folder at the repository root (it already is in this workspace).
2. Commit and push to GitHub (main branch). The included workflow will build and publish the contents of `lushy-site/` to GitHub Pages automatically.
   - Site URL will be: `https://<username>.github.io/<repo-name>/lushy-site/` or (if this repo is named `lushy-site`) `https://<username>.github.io/lushy-site/`.

Editing theme colors
- Open `css/style.css` and modify the CSS variables at the top (under `:root`) — for example `--primary-color`, `--accent-color`, `--bg-color`, `--font-family`, `--glass-blur`.

Configuring the Departures API
- The departures widget uses the public endpoint `https://api.departureboard.io/2.0/departures?station=NOT` by default. Edit the endpoint in `js/departures.js` (the `API` constant) to change station or provider.
- Note about CORS: Some public departure APIs may block cross-origin requests from static pages. If you see a CORS/network error, the page will show fallback sample data. For production, consider using a small proxy (or host the site on a domain with an API key-enabled service).

Accessing the secret dashboard
- The secret gateway supports two methods:
  - URL token: visit `secret.html?token=letmein` (default token). This will unlock the dashboard and set an auth flag in `localStorage`.
  - Password prompt: open `secret.html` and click "Unlock". The default password is `lushy2025`.
- Both the token and password are defined in `secret.html` for simplicity. For better security, change them before pushing the repo.

Local-first privacy
- The dashboard stores auth, to-dos and notes in the browser's `localStorage`. There is no server-side authentication.

GitHub Pages deployment
- The included workflow `.github/workflows/deploy.yml` packages the `lushy-site/` folder and uses the official `actions/upload-pages-artifact` and `actions/deploy-pages` steps to publish to GitHub Pages on push to `main`.
- Make sure GitHub Pages is enabled for the repository (the Actions workflow will publish to the `gh-pages` environment automatically).

Customization ideas
- Add your real social links in `social.html`.
- Replace `assets/logo.svg` and `favicon.svg` with your own images.
- Replace the secret token/password with something unique.

Troubleshooting
- If the departures feed shows sample data, the API likely blocked CORS or the endpoint changed. Try a different public API, or host a proxy.

License
- Use or adapt freely for personal projects.
