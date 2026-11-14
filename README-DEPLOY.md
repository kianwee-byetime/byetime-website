# Byetime.AI website: deploy guide

This folder is the complete website. Plain HTML, no build step.

    index.html      the whole page
    images/         logos, app icons, founder photos
    vercel.json     redirects old pages (/services/..., /about) to the new page
    robots.txt      lets Google crawl the site

## 1. Deploy on Vercel

The domain byetime.ai is already connected to a Vercel project through GoDaddy DNS,
so use that same project. Do not create a new one, or you will have to move the domain.

If the project is connected to a GitHub repo:
1. Back up the current repo (make a branch called `old-site`).
2. On `main`, delete the old site files and copy in everything from this folder.
3. In Vercel > Project > Settings > Build & Deployment, set:
   Framework Preset: Other. Build Command: empty. Output Directory: empty (or `.`).
4. Commit and push. Vercel deploys automatically.

If the project was deployed by drag-and-drop or the CLI (no repo):
1. Install the CLI: `npm i -g vercel`, then `vercel login`.
2. In this folder run `vercel link` and choose the existing byetime project.
3. Run `vercel --prod`.

After deploying, open https://www.byetime.ai on desktop and phone and check:
- every nav link scrolls to its section
- the WhatsApp button opens a chat with +60 17-3133 284
- an old link like https://www.byetime.ai/services/wms lands on Our Services

## 2. WhatsApp button

Already built in (bottom-right corner). It opens WhatsApp to +60 17-3133 284 with a
pre-filled message. To change the number or message, search index.html for `wa.me`.

## 3. Contact form to email

The form sends to kianwee@byetime.ai through FormSubmit (free, no account).

One-time activation, required:
1. After deploying, submit the form once on the live site with a test message.
2. FormSubmit emails kianwee@byetime.ai an activation link. Click it.
3. Check spam if it doesn't arrive. Until it's activated, nothing is forwarded.

Recommended after activation: FormSubmit gives you a random alias string. In
index.html, replace `kianwee@byetime.ai` in the FORM_ENDPOINT line with that alias, so
your email address isn't visible to spam bots in the page source.

If a submission ever fails, visitors are told to WhatsApp you instead.

## Still to do (not blocking launch)
- Privacy policy page (PDPA). The form already shows a consent line.
- Official Accounting icon from the Odoo partner kit (images/accounting.png).
- Favicon and a link-preview image (og:image).
- Vercel Analytics: Project > Analytics > Enable.
- Google Search Console: add byetime.ai and submit https://www.byetime.ai/.
