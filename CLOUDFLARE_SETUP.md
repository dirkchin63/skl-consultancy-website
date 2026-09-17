# Cloudflare and Hostinger deployment

This repository is prepared for the same deployment pattern as `wmc-hk.com`:

- GitHub `main` is the source of truth.
- Cloudflare Workers Builds deploys the static site from `dist/`.
- Cloudflare becomes the authoritative DNS provider.
- Hostinger remains the domain registrar and continues any existing email services.

## Cloudflare Worker

1. Add `skl-consultancy.com` to the same Cloudflare account used by `wmc-hk.com`.
2. Copy every existing DNS record into Cloudflare. Preserve MX, SPF, DKIM and DMARC records.
3. In Cloudflare, open **Workers & Pages → Create application → Import a repository**.
4. Select `dirkchin63/skl-consultancy-website` and use:
   - Production branch: `main`
   - Build command: `npm run build`
   - Deploy command: `npm run deploy`
   - Root directory: `/`
5. The Worker name must be `skl-consultancy-website`, matching `wrangler.jsonc`.
6. Check the generated `workers.dev` preview before attaching the production domains.

## Hostinger

After Cloudflare has imported and reviewed the existing DNS records, replace the domain's
Hostinger nameservers with the two nameservers assigned by Cloudflare. Do not remove or
alter Hostinger email subscriptions or the corresponding MX, SPF, DKIM and DMARC records.

Keep the existing Hostinger website DNS records in Cloudflare during this step so the old
website continues to work while the Worker preview is tested.

## Production domain cutover

Only after the Worker preview passes testing, add these custom domains to the Worker:

- `skl-consultancy.com`
- `www.skl-consultancy.com`

Cloudflare will create the required proxied DNS records and SSL certificates. Remove or
replace only the old website A/CNAME records; leave all email records unchanged.

## Cutover checks

- Test the `workers.dev` preview before changing nameservers.
- Confirm Traditional Chinese, Simplified Chinese and English pages.
- Confirm both WhatsApp numbers and the contact form.
- Confirm the apex and `www` domains redirect/serve consistently over HTTPS.
- Keep the old Hostinger website available until DNS propagation and SSL are complete.
