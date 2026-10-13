# Fold & Form Works

Made-to-order V-grooved and folded sheet metal: configurator, 3D prototype, laser engraving, cart and checkout. One self-contained page (`index.html`), no build step.

## Put it on GitHub Pages (free)

1. Create a new repository on GitHub, for example `foldform-site`.
2. Upload every file in this folder to the repository root (drag them into **Add file → Upload files**). Keep `.nojekyll`.
3. Go to **Settings → Pages**. Under **Source** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/foldform-site/`.

### Custom domain
1. In **Settings → Pages → Custom domain**, enter your domain (for example `www.foldform.hk`) and tick **Enforce HTTPS**.
2. At your domain registrar, add a `CNAME` record for `www` pointing to `<your-username>.github.io`.
3. Replace `example.com` in `robots.txt`, `sitemap.xml` and the commented lines near the top of `index.html`.

## What works on a static host
Everything you see: the scroll animations, the 3D prototype, the configurator and design checks, the language and currency switches, engraving previews and the cart. The cart is stored in the visitor's browser.

## What needs a server before you take real orders
GitHub Pages only serves files, so three things need a small backend. The simplest route is to host the same repository on **Vercel** or **Netlify** (both free to start and deploy straight from GitHub) and add serverless functions:

1. **Payments.** Create a Stripe Checkout Session in a function that recalculates the price on the server, then redirect the customer to Stripe. Never trust the price sent from the browser. FPS, PayMe and Alipay HK need a local gateway or Stripe's supported methods.
2. **Order emails.** Send the order (product, dimensions, material, finish, engraving, fixing, pick-up or delivery) to your team and a confirmation to the customer.
3. **Uploads.** Customer photos, logos and sketches must be uploaded to storage (for example Cloudinary, S3 or Vercel Blob) and linked to the order. Today they only stay in the visitor's browser.

## Where to change things in `index.html`
| What | Search for |
|---|---|
| Brand name on the engraved hero | `const BRAND=` |
| Markup on factory cost | `MARKUP=` |
| Factory sheet prices (HK$ per sq ft) | `const MATS=` |
| Minimum charge / fold cost | `MIN_SQFT=` / `FOLD_COST=` |
| Engraving, holes, slots, wall rail prices | `ENG_UNIT=`, `HOLE=`, `SLOT=`, `CLEAT=` |
| Showroom addresses | `const LOCS=` |
| English / Chinese text | `const T={` |
| Products and their size ranges | `const PRODUCTS=[` |
