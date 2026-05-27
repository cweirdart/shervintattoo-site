# Stripe Payment Links — Shop Wiring Handoff

**For:** Claude Code  
**Repo:** `cweirdart/shervintattoo-site`  
**Site:** shervintattoo.com (static HTML, Netlify, auto-deploys on push to `main`)  
**Date:** May 26, 2026

---

## What needs to happen

Wire the shop section of `index.html` so each product's "Buy" button links to a Stripe Payment Link. Shervin (the client) will create his own Stripe account and generate payment links for each product. The HTML should be ready for him to paste in URLs.

## Decisions already made

- **Payment platform:** Stripe Payment Links (no monthly fee, 2.9% + 30¢ per transaction)
- **Shervin creates his own Stripe account** — do NOT use any existing Stripe account
- **No storefront redirect** — checkout happens via Stripe's hosted checkout page, but the shop UI stays on shervintattoo.com
- **All 4 products are currently "Sold out"** — the wiring should make it trivial to toggle between sold out and available
- **Future state:** A client-facing web editor with Stripe integration is planned, but this is the working solution for now

## Current shop section (index.html, lines ~1830–1882)

4 products, all sold out:
1. Limited Edition Flash Sheet 1/50 — $80
2. "DIASPORA" Limited Edition Shirt — $40
3. Stoneware Vessel Vol. 1 — $120
4. Original Sketches — $100

**Bug to fix:** Item 4 has a malformed img tag (duplicated `<img src="tiger-sketch.jpg"`):
```html
<div class="shop-item-image"><img src="tiger-sketch.jpg" <img src="tiger-sketch.jpg" alt="Original Sketch — tiger sketch"></div>
```
Fix this to a single proper img tag.

## What to change

### 1. Change buy buttons from `<button>` to `<a>` for available items

When a product is **available**, the buy button should be an `<a>` tag linking to the Stripe Payment Link:
```html
<a href="YOUR_STRIPE_PAYMENT_LINK_HERE" target="_blank" rel="noopener" class="btn-buy">Buy Now</a>
```

When **sold out**, keep as-is:
```html
<button class="btn-buy sold-out" disabled>Sold Out</button>
```

### 2. Add CSS for `a.btn-buy`

The existing `.btn-buy` styles are on `button` elements. Add matching styles so `<a>` tags render identically:
```css
.shop-item-info .btn-buy {
  /* existing styles already use class selector, should work for both */
  /* just add: */
  text-decoration: none;
}
```

### 3. Update EDIT comments

Replace the existing shop EDIT comment block (lines ~1831-1838) with clearer instructions that cover the Stripe Payment Link workflow:

```
EDIT: SHOP — manage products and payment links.

  TO MAKE AN ITEM AVAILABLE:
  1. Create a Stripe Payment Link at dashboard.stripe.com/payment-links
  2. Replace the <button> with:
     <a href="https://buy.stripe.com/YOUR_LINK" target="_blank" rel="noopener" class="btn-buy">Buy Now</a>

  TO MARK AS SOLD OUT:
  Replace the <a> with:
     <button class="btn-buy sold-out" disabled>Sold Out</button>

  TO ADD A PRODUCT IMAGE: replace <div class="shop-item-image">Sold out</div>
  with <div class="shop-item-image"><img src="your-image.jpg" alt="Product name"></div>
  
  TO ADD A NEW PRODUCT: copy an entire <div class="shop-item">...</div> block.
  TO REMOVE A PRODUCT: delete the entire <div class="shop-item">...</div> block.
```

### 4. Update ONBOARDING.md

Add a "Shop & Payments" section explaining:
- How to create a free Stripe account (stripe.com)
- How to create a Payment Link in the Stripe Dashboard (Products → Add Product → Create Payment Link)
- How to enable shipping address collection on the payment link
- How to paste the URL into the HTML buy button
- How to toggle sold out / available
- Where order notifications go (Stripe emails him automatically)

## Do NOT change

- Product names, prices, or descriptions
- The shop grid layout or card styling
- The visual design (dark parchment theme)
- Any other section of the site
- Leave all 4 items as "Sold out" — just make them ready to be toggled on when Shervin has his Stripe links

## Style guide reference

See `STYLE-GUIDE.md` for the full design system. Key tokens:
- `--color-ink` for text/borders
- `--color-ink-ghost` for disabled/sold-out state
- `--color-paper` for backgrounds
- `--font-mono` (JetBrains Mono) for button text
- Buttons: uppercase, letter-spacing 0.1em, 0.68rem font size

## Testing

After changes, verify:
- All 4 items still show "Sold Out" with line-through styling
- No visual changes to the shop section
- The duplicate img tag on item 4 is fixed
- EDIT comments are clear and accurate
- ONBOARDING.md shop section reads well for a non-technical person
