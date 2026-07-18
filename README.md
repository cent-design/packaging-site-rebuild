# Yucca Packaging — Static Site

A self-contained static rebuild of yucca.co.za: HTML, CSS, JS, fonts, and images pulled
directly from the live WordPress/WooCommerce site and served without a backend.

## Structure

- Top-level `*.html` files and slug directories (e.g. `about.html`, `product/<slug>/`,
  `sustainable-packaging-south-africa/`) mirror the site's page URLs.
- `wp-content/`, `wp-includes/` hold the original theme, plugin, and upload assets
  (CSS, JS bundles, fonts, images) referenced by the pages.
- `shop?product_cat=<name>.html` / `shop?packaging_type=<name>.html` are the shop's
  category/type filter views, kept as separate static pages.

## What's excluded

- `wp-admin/`, `wp-json/`, and login/checkout backend routes (no server to power them).
- Near-duplicate WooCommerce product-variant pages (e.g. `?pa_volume=250ml`) — their
  content is identical to the base product page aside from which swatch is
  pre-selected, so links to them now point at the canonical product page instead.

## Running locally

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.
