# UNBOTHERED CLOTHING — E-Commerce Platform (Prototype)

A complete multi-page, data-driven fashion e-commerce application for the UNBOTHERED brand:
storefront + content platform + services + admin CMS, in dependency-free HTML/CSS/JS.

## Run it

Static files use absolute paths (`/css/...`), so serve the folder over HTTP:

```bash
cd unbothered
python -m http.server 8000
# open http://localhost:8000
```

## Access

| Area | URL | Credentials |
|---|---|---|
| Storefront | `/` (index.html) | — |
| Admin CMS | `/admin.html` | password: `admin123` |
| Customer account | `/account.html` | `demo@unbothered.ng` / `demo123` |
| Test coupon | apply in cart | `WELCOME10` (10% off over ₦50,000) |

## Structure

```
├── index.html  shop.html  product.html  collection.html  collections.html
├── search.html  cart.html  checkout.html  wishlist.html  account.html
├── lookbook.html  journal.html  article.html  reviews.html
├── custom-order.html  custom-track.html  personal-styling.html
├── ai-stylist.html  wardrobe.html  outfit-analyzer.html
├── about.html  sustainability.html  community.html  stores.html
├── faq.html  size-guide.html  shipping.html  returns.html  contact.html
├── privacy.html  terms.html  404.html  admin.html
├── css/style.css          # design system (navy/gold, editorial)
├── js/data.js             # CMS seed database (products, content, orders…)
├── js/store.js            # data-access layer + cart/wishlist/search/UI
├── js/admin.js            # admin dashboard (13 CMS modules)
├── assets/                # logo, favicon (replace with brand photography)
├── robots.txt  sitemap.xml
└── README.md
```

## Architecture: ADMIN → DATABASE → STOREFRONT

All storefront and admin code reads/writes through `js/store.js` (`DB`), which
currently persists to `localStorage`. In production, swap the internals of `DB`
for `fetch()` calls to a backend (e.g. Supabase/PostgreSQL + API) — no page code changes.

Admin edits (products, homepage, reviews, orders, coupons, media, collections,
journal, settings) are reflected on the customer site immediately after save.

## Prototype vs production (honest status)

- **Functional end-to-end (demo data):** routing, search, filters, product pages,
  cart, coupons, checkout flow with order creation, wishlist, account, review
  submission + moderation, custom orders + tracking, AI stylist (rule-based),
  admin CMS.
- **Simulated, clearly labeled:** payments (Paystack/Flutterwave/Stripe choice is
  recorded on the order; no real charge), AI vision tools (demo analysis),
  image uploads (filename recorded only).
- **Not connected (needs credentials):** payment providers, AI APIs, social
  platform APIs, analytics pixels, email/SMS/WhatsApp gateways.
- **Placeholder visuals:** product/collection imagery is CSS-generated art
  direction. Replace by rendering `<img>` from the media library records.

## Data reset

Admin sidebar → "Reset demo data" (clears localStorage back to seed).
