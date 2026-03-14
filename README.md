Visual Analytics IMDb Dashboard
===============================

A lightweight static web dashboard that visualizes IMDb data using D3, Crossfilter, and DC.js. The UI is a single-page visualization loaded from local CSV data files in the repository.

What you get
- A set of charts rendered in a single HTML file (`index.html`).
- Data files at the repo root:
  - `movies_imdb.csv`
  - `movie_metadata_orig.csv`
- Simple, dependency-free static server for local development.

Forking and running locally
- Fork this repository on GitHub to your account.
- Clone your fork locally:
  - `git clone https://github.com/your-username/visual_analytics.github.io.git`
- Install a lightweight static server (the project includes an npm script for convenience):
  - If you have Node.js and npm installed, run: `npm install`.
- Start the local dev server:
  - `npm run serve`
- Open the app in your browser:
  - http://localhost:8080/index.html
- If port 8080 is in use, update the port in `package.json` (see below) or run with a different port:
  - Example: `http-server -p 8081 -c-1` (manual), or change the script to another port.

Customizing and deploying
- Data files: Ensure `movie_metadata_orig.csv` and `movies_imdb.csv` exist at the repository root for the charts to render. If you rename them, update their references in the code accordingly.
- Production deployment (static hosting): You can deploy the contents of this repo to any static hosting service (GitHub Pages, Netlify, Vercel, Apache/Nginx, etc.). Since the app is static, it does not require a backend. For a server-based host, simply serve the repository as a static site.
- If you plan to run behind a domain, you may want to configure your web server to serve from the repository directory and ensure proper MIME types for CSS/JS.

Development notes
- The app currently loads data from local CSV files via HTTP requests. If you move to a different hosting environment, ensure the CSVs are accessible at the same relative paths.
- The UI is contained in `index.html` with an embedded script that wires up the charts. For large projects, consider modularizing into smaller JS files (data.js, charting.js, ui.js).

Usage tips
- To restart after code changes, stop the server (Ctrl+C) and run `npm run serve` again.
- If you want to test a quick change without npm, you can install a global server and run it from the repo root:
  - `npx http-server -p 8080 -c-1`

- Feel free to open issues or submit pull requests with improvements such as:
Contributing
- Feel free to open issues or submit pull requests with improvements such as:
- Feel free to open issues or submit pull requests with improvements such as:
  - Modularizing the JavaScript into smaller files
  - Adding tests for any data processing helpers
  - Improving accessibility (ARIA labels, keyboard navigation)
  - Enhancing responsiveness for mobile layouts

Notes
- This repository may load the CSV data from the repo. If the data files are large or unavailable, charts may fail to render or appear incomplete.
- If you want me to patch in a sample CSV for quick demos, tell me and I’ll add a lightweight dataset.

License
- The license for this repository is not specified in this document. Please add an appropriate license header in your fork if you plan to share publicly.

Quick Start: Deploying to Common Hosts

- GitHub Pages (static hosting)
  - Push this repository to a GitHub repository.
  - In GitHub, go to Settings > Pages, set Source to the branch you push (eg. main) and root (/).
  - Save; your site will be served at https://<your-username>.github.io/<repository-name>/ or the root if you host from root.
  - Notes: For this repo, the index.html and assets at root are served as a static site. Ensure movie_metadata_orig.csv is present at the root for the charts to load.

- Netlify
  - Create a Netlify site from Git, select the repository and branch (main).
  - Build settings: Leave defaults; Publish directory: ./
  - Netlify will provide a URL to access the site after deployment.

- Vercel
  - Import Project from Git provider, choose the repository.
  - Default settings should work for a static site. Deploy and use the provided URL.

- Firebase Hosting
  - Install: npm i -g firebase-tools
  - Login: firebase login
  - Init: firebase init hosting (choose public directory as "." and configure as a single-page app if prompted)
  - Deploy: firebase deploy

- General notes
  - Ensure all static assets (css, js, data CSVs) are included in the published directory.
  - If you host on a domain, configure your hosting to serve from the repository root and ensure MIME types for JS/CSS are served correctly.
