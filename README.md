# PLOTIVY.APP Netlify Site

This is a minimal static site configured for Netlify to serve your Streamlit Cloud app at:

- https://plotivy.streamlit.app/

By default, the `_redirects` file is set up to proxy all requests through Netlify to your Streamlit app and keep `plotivy.app` in the address bar. Alternatively, you can switch to a 301 hard redirect.

Contents:

- `_redirects` — Netlify rules. Currently: `200!` proxy to Streamlit. Uncomment the `301!` line if you prefer a hard redirect.
- `index.html` — Fallback meta-refresh + manual link (only used if you switch to 301 or disable the proxy).

## Deploy to Netlify

You have two easy options:

1. Connect the repo (recommended)

   - Push this folder as the repo root (it already is).
   - In Netlify: Add new site → Import from Git → pick the repo.
   - Build command: (leave empty)
   - Publish directory: `/` (repo root)
   - Deploy.

2. Drag-and-drop
   - Zip these files or select the folder, then drag onto the Netlify UI (Sites → Add new site → Deploy manually).

## Custom domain: plotivy.app

1. In Netlify → Site settings → Domain management → Add custom domain → enter `plotivy.app`.
2. Choose one of:
   - Use Netlify DNS (recommended): point your domain’s nameservers to Netlify and let it create the records.
   - Keep your current DNS provider: create the DNS records that Netlify shows you (CNAME/ALIAS for root via ANAME/ALIAS if supported, and `www` CNAME to your Netlify site).
3. Wait for DNS to propagate. Netlify will then provision a free Let’s Encrypt certificate for HTTPS.

## Proxy vs Redirect

- Proxy (current): `/* https://plotivy.streamlit.app/:splat 200!` keeps `plotivy.app` in the URL. Great for a seamless branded domain. If Streamlit sets strict CSP headers or blocks being proxied, switch to redirect.
- Redirect: `/* https://plotivy.streamlit.app/:splat 301!` changes the address bar to `streamlit.app` immediately. Simplest and most robust.

## Notes

- No build step is needed; this is a static deploy.
- If you run into issues with WebSockets or SSE over the proxy (rare), switch to the 301 redirect line and redeploy.
