# PLOTIVY.APP Netlify Redirect Site

This folder is a minimal static site designed for Netlify. It permanently redirects all traffic to the Streamlit Cloud app at:

- https://plotivy.streamlit.app/

Contents:

- `_redirects` — Netlify redirects configuration preserving path and query.
- `index.html` — fallback meta refresh and manual link to the Streamlit app.

Deploy this folder via Netlify (publish directory = `netlify`). If you’re using a separate GitHub repo (`fravil92/PLOTIVY.APP`), copy these files there as the repo root or keep them in a `netlify/` subfolder and set the publish directory accordingly.
