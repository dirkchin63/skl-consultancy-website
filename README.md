# SKL Consultancy website

Static, GitHub-maintainable rebuild of `skl-consultancy.com`.

## Edit content

- Text, services, people and contact details: `dist/data.js`
- Page structure and behaviour: `dist/app.js`
- Colours and layout: `dist/styles.css`
- Images: `dist/assets/`

After changing the shared HTML shell, run `node scripts/build-routes.mjs`.
The deployable website is the `dist/` folder and can be hosted on GitHub Pages or Cloudflare Pages.
