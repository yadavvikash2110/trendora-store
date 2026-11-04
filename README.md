# Trendora demo storefront

A responsive, static multi-page storefront concept for **Trendora** with Home, Fashion, Decorations and Perfumes pages, sample product listings, a local-storage shopping bag and a demonstration checkout.

## Open the website

- Extract `Trendora-Website.zip`.
- Open `index.html` in a modern browser, or run a simple local web server from this folder (recommended):

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Included

- `index.html` — homepage and featured products
- `fashion.html`, `decorations.html`, `perfumes.html` — separate category pages
- `checkout.html` — demo-only checkout and sample order confirmation
- `assets/css/styles.css` — responsive styling
- `assets/js/products.js` — sample catalogue and image URLs
- `assets/js/app.js` — product rendering, search/sort, cart and demo checkout
- `PAYMENT_SETUP.md` — real payment, hosting and launch guidance
- `robots.txt`, `sitemap.xml` — search-engine starter files

## Important limitations

This is a front-end prototype, not a production ecommerce system. Cart data is stored in the visitor's browser. Orders are not sent to a server. No user account, inventory database, tax calculation, shipping integration, email/SMS, admin panel, analytics or real payment gateway is connected. The sample catalogue, prices and images are placeholders. Remote product photography is loaded from Unsplash URLs, so an internet connection is needed for those images and Google Fonts.

Do not collect real customer data or accept real orders with this demo checkout. For production, add a secure backend or move the catalogue and checkout to a maintained ecommerce platform, then follow `PAYMENT_SETUP.md`.

## Customise products

Edit `assets/js/products.js`. Each product has an `id`, `category`, `name`, `description`, `price` (INR), `tag` and `image` URL. Keep IDs unique. Replace all sample content and ensure you have permission to use every image.

## Publish with Netlify (simple static hosting)

1. Create/sign in to a Netlify account.
2. Extract the ZIP on your computer.
3. Drag the extracted `trendora` project folder (or its contents) into Netlify's manual deploy/drop area.
4. Netlify will provide a temporary site URL. Add a custom domain if you own one and configure HTTPS.
5. Replace `YOUR-DOMAIN` in `sitemap.xml` and `robots.txt` with the exact live domain, including the chosen `www` or non-`www` form.

Netlify deploy guide: https://docs.netlify.com/deploy/create-deploys/

## Publish with GitHub Pages

1. Create a GitHub repository and upload the contents of this folder.
2. In repository Settings → Pages, select the publishing source/branch and root folder.
3. Save and wait for GitHub Pages to publish the static files.
4. Add a custom domain if desired, configure DNS and HTTPS, then update the sitemap and robots file with the canonical live domain.

GitHub Pages guide: https://docs.github.com/en/pages/quickstart

## Google Search indexing

1. Publish the website first on a stable HTTPS domain.
2. Replace the `YOUR-DOMAIN` placeholders in `sitemap.xml` and `robots.txt` with the exact canonical domain.
3. Check that the public pages load and are not blocked by a `noindex` tag or robots rule. Checkout intentionally has `noindex`.
4. Open Google Search Console: https://search.google.com/search-console/ and add/verify your domain or URL-prefix property.
5. Submit `https://YOUR-DOMAIN/sitemap.xml` in Search Console's Sitemaps report (using your actual domain).
6. Use URL Inspection for the homepage and category pages and request indexing where available.
7. Keep product descriptions unique and useful, use accurate page titles, compress images, add real business/contact/policy pages, and maintain working internal links.

Submitting a sitemap or requesting indexing is a discovery request, not a guarantee of inclusion or ranking. Google may take days or weeks to crawl pages.

Google Search Central: https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap
Request recrawl: https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl

## Before a real launch

Read `PAYMENT_SETUP.md`. You still need a legal business identity, verified payment gateway, backend order/payment verification, real shipping and returns policies, tax setup, customer support, inventory management and order fulfilment. Nothing in this ZIP has been deployed or connected to live payments.
