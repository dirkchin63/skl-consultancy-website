# SKL Consultancy website

Static, GitHub-maintainable rebuild of `skl-consultancy.com`.

## Edit content

- Text, services, people and contact details: `dist/data.js`
- Page structure and behaviour: `dist/app.js`
- Colours and layout: `dist/styles.css`
- Images: `dist/assets/`

After changing the shared HTML shell, run `node scripts/build-routes.mjs`.
The deployable website is the `dist/` folder and is configured for Cloudflare Workers.

## Cloudflare deployment

The repository is configured for Cloudflare Workers Builds, matching the deployment model
used by `wmc-hk.com`. Cloudflare serves the static assets in `dist/`, while Hostinger can
remain the domain registrar and email provider. See `CLOUDFLARE_SETUP.md` for the one-time
Cloudflare and Hostinger connection steps.
