# backforty-software-site

The marketing/sales site for Back Forty Software (`BackFortySoftware.com`), Warren's software/apps business, split out of 5 Acre Studios on 2026-07-25.

## Stack

Plain static HTML + one shared stylesheet, no build step, no framework, no JavaScript. Deployed to Vercel as a static site.

## Structure

```
index.html                                       -> homepage
products/index.html                              -> product catalog
products/<product-slug>/index.html                -> one product's sales page
products/<product-slug>/download/index.html        -> post-purchase download page
downloads/<product-slug>.zip                       -> the actual customer download
assets/style.css                                   -> shared styles for every page
```

## Adding a new product

1. Copy `products/shoot-proposal-skill/` (both `index.html` and `download/index.html`) into a new `products/<slug>/` folder and rewrite the content.
2. Add the customer-facing download file to `downloads/`.
3. Add a card for it to `products/index.html`.
4. Create a Square Payment Link for it (Warren's Square account) and wire the checkout button + redirect-after-checkout URL to `/products/<slug>/download/`.

## Checkout

No custom checkout code. Each product's "Buy now" button points at a Square Payment Link created directly in Square's dashboard. Square doesn't auto-deliver digital files, so each Payment Link is set to redirect to that product's `/download/` page after successful payment, and the same download link is also pasted into Square's order-confirmation email template as a backup.

## Known limitation

Download links under `/downloads/` are unlisted, not access-gated. Anyone with the direct URL could download without paying. Acceptable for now at this price point and product count; revisit if it becomes a real problem.
