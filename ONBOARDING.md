# How to Edit Your Website

**Site:** https://shervintattoo.com
**Repo:** https://github.com/cweirdart/shervintattoo-site
**Built by:** c.weird (info@cweird.com)

---

## How it works

Your website is one file: `index.html`. It lives on GitHub. Every time you make a change and save it, Netlify automatically updates the live site within about 60 seconds.

You have **two ways** to make changes. Both are free. Pick whichever feels more comfortable.

### Option 1 — All in your browser with github.dev (simpler, recommended)

Edit code AND add/remove photos in one place — your web browser. Nothing to install. Nothing local to sync. Zero risk of "is this version up to date?" confusion.

**How to open it:**
1. Go to **github.com/cweirdart/shervintattoo-site** in any browser
2. Press the **period key (`.`)** on your keyboard
3. The page transforms into a full code editor (VS Code in the browser)

That's it. Skip ahead to the section "Editing in github.dev (browser-only workflow)" below.

### Option 2 — GitHub.com web editor + GitHub Desktop (two tools)

Use the **github.com website** to edit code, and the **GitHub Desktop app** to add/replace/delete photos and videos.

This is the setup you're already on. It works, but you have to remember to **Fetch origin in GitHub Desktop before doing any local work** so your computer's copy stays in sync with the website. See "The one rule: Fetch before local changes" below.

---

## Setup (one time only)

You've already done this:

1. ✅ GitHub account created
2. ✅ Collaborator invite accepted
3. ✅ GitHub Desktop installed (only needed for Option 2)
4. ✅ Repository cloned to your computer (only needed for Option 2)

Your site files are now in a folder on your computer. To find it: open GitHub Desktop → **Repository → Show in Finder** (Mac) or **Show in Explorer** (Windows).

If you go with Option 1 (github.dev) you don't need GitHub Desktop or the local folder at all — but keep them around in case you want them later.

---

## Your first edit (do this once to learn the loop)

Try a no-risk practice change so you can feel the whole workflow before doing anything important. Just change the copyright year in the footer.

**In github.dev:**
1. Open github.com/cweirdart/shervintattoo-site → press `.`
2. In the left file tree, click `index.html`
3. Press `Cmd+F` (Mac) or `Ctrl+F` (Win), search for `EDIT: FOOTER`
4. Change the year to next year and back
5. Click the **Source Control icon** on the left rail (looks like a branching tree) — third icon down
6. Type a commit message like "test: footer year"
7. Click **Commit & Push** (or the checkmark)
8. Open shervintattoo.com — within 60 seconds, scroll to the footer to see your change

That's the entire workflow. If that worked, you can edit anything. If something feels off, scroll to "If something breaks" below.

---

## Editing text, prices, or code

Pick one of the two paths depending on what you set up:

### Path A — In github.dev (browser-only, recommended)

1. Go to **github.com/cweirdart/shervintattoo-site** → press **`.`**
2. Click `index.html` in the left file tree
3. Press **Cmd+F** (Mac) or **Ctrl+F** (Windows) and search for **EDIT:** to jump between editable sections
4. Make your changes — github.dev auto-saves them as you type (you'll see a dot on the file tab when there are unsaved changes)
5. Click the **Source Control icon** (3rd icon down on the left rail, looks like a branch)
6. Type a short note (e.g., "updated flash sheet price")
7. Click **Commit & Push** (or press `Cmd+Enter` / `Ctrl+Enter`)
8. Wait ~60 seconds, refresh shervintattoo.com — your change is live

### Path B — On github.com (classic web editor)

1. Go to **github.com/cweirdart/shervintattoo-site**
2. Click on **index.html**
3. Click the **pencil icon** (top right of the file) to edit
4. Press **Cmd+F** (Mac) or **Ctrl+F** (Windows) and search for **EDIT:** to jump between editable sections
5. Make your changes
6. Click **Commit changes** (green button, top right)
7. Add a short note about what you changed (e.g., "updated flash sheet price")
8. Click **Commit changes** again to confirm
9. Wait about 60 seconds, then refresh shervintattoo.com — your change is live

Both paths end the same way: a commit on the `main` branch triggers an auto-deploy.

---

## What you can edit

Every editable spot in `index.html` has an `EDIT:` comment next to it. Here's what to search for:

| Search for | What you'll change |
|---|---|
| `EDIT: SEO` | Page title and Google description |
| `EDIT: HERO` | Tagline, location, button text |
| `EDIT: ABOUT` | Bio, studio name and address, specialties |
| `EDIT: GALLERY ITEMS` | Add or remove portfolio images/videos |
| `EDIT: FILTER BUTTONS` | Gallery filter tabs |
| `EDIT: BOOKING` | Booking form text and options |
| `EDIT: SHOP` | Product names, prices, sold out status |
| `EDIT: CONTACT` | Email address, Instagram link |
| `EDIT: FOOTER` | Copyright year |
| `EDIT: COLORS` | Site colors |
| `EDIT: FONTS` | Fonts |

---

## How to edit text

Find the section and change the words between `>` and `</`. Example:

**Before:**
```
<p class="hero-tagline">Gifts from West Asia and the West Coast.</p>
```

**After:**
```
<p class="hero-tagline">Your new tagline here.</p>
```

Only change the text. Don't touch the tags around it.

---

## HTML safety — read this once, save yourself headaches

When you go beyond just changing text — adding a photo, swapping a link, etc. — these are the rules to remember:

### Rule 1 — Quotes around values are mandatory

Whenever you see `something="value"`, the quotes MUST stay around the value. Removing them breaks the line.

| ✅ Correct | ❌ Broken |
|---|---|
| `<img src="photo.jpg" alt="A tattoo">` | `<img src=photo.jpg alt=A tattoo>` |
| `<a href="https://instagram.com/shervin.510">` | `<a href=https://instagram.com/shervin.510>` |
| `<div class="shop-item">` | `<div class=shop-item>` |

If you're not sure, **just copy a working line from elsewhere in the file** and only change the specific parts you need.

### Rule 2 — File names need to be exactly right

The text inside `src="..."` must match the actual filename **exactly** — same letters, same dashes, same case, same extension.

- Use lowercase letters and hyphens: `tiger-sketch.jpg`, not `Tiger Sketch.jpg`
- Avoid spaces in filenames. If a filename does have a space, replace it with `%20` in the code (e.g., `src="Work/22%20my-photo.jpg"`)
- Watch the file extension: `.jpg` ≠ `.JPG` ≠ `.jpeg`

### Rule 3 — `&` in text needs to be `&amp;`

If you want to display the **&** symbol in text, type `&amp;` instead. Example: `Black &amp; Grey`. (HTML uses `&` for special characters, so a bare `&` confuses the browser.)

### Rule 4 — Don't delete the closing tag

Every opening tag like `<p>` or `<div>` has a matching closing tag like `</p>` or `</div>`. Delete one without the other and the layout breaks.

### Rule 5 — When swapping tag types, change BOTH ends

If you swap a `<button>` for an `<a>` (or vice versa, like when toggling sold-out on a shop item), the closing tag has to change too:

| ✅ Correct | ❌ Broken |
|---|---|
| `<a href="...">Buy Now</a>` | `<a href="...">Buy Now</button>` |
| `<button class="btn-buy sold-out" disabled>Sold Out</button>` | `<button class="btn-buy sold-out" disabled>Sold Out</a>` |

If you only change the opening tag, the browser sees mismatched tags and the page layout can go strange.

---

### Stuck or unsure? Two safe escape hatches

1. **Copy a working line and only edit what you need to.** This is the single best way to avoid syntax mistakes.
2. **Ask an AI to write the line for you.** Paste the surrounding 2-3 lines into claude.ai or chatgpt.com and say "rewrite this so the image points to my-new-file.jpg." Then paste the answer back. It'll be correct.

---

## Adding or removing photos and videos

Adding a gallery photo means doing **two** things: (1) get the file into the `Work` folder, and (2) add the code line that displays it. Do both, commit, you're done.

### Before you start: keep photos under 2 MB

Photos larger than 2 MB can fail to load on older phones. If your photo is bigger, ask any AI chat (Claude, ChatGPT) to resize it, or use Preview on Mac (Tools → Adjust Size → set width to 1600px).

---

### Path A — All in github.dev (browser-only)

**Adding a new photo:**

1. Open github.com/cweirdart/shervintattoo-site → press `.`
2. In the left file tree, expand the **`Work`** folder
3. **Drag your photo** from Finder/Explorer directly into the `Work` folder in the file tree
4. Rename the file in the tree (right-click → Rename) to start with the next number, e.g., `22 my-new-tattoo.jpg`
5. Open `index.html`, search for `EDIT: GALLERY ITEMS`
6. Copy any existing gallery line, paste it where you want the new image, and edit the filename — **replace spaces with `%20`**:

```
<div class="gallery-item" data-category="black-and-grey"><img src="Work/22%20my-new-tattoo.jpg" alt="Tattoo work by Shervin" loading="lazy"></div>
```

7. Set the category (see "Categories" below)
8. Click the Source Control icon → write a message ("add new tattoo photo") → Commit & Push

Both the photo upload and the code change push together in one commit. Done.

**Removing a photo:**
1. In the `Work` folder file tree, right-click the file → **Delete**
2. In `index.html`, delete the entire matching `<div class="gallery-item">...</div>` line
3. Commit & push

**Replacing a photo (keep position, swap image):**
1. Drag the new photo into the `Work` folder
2. github.dev will ask if you want to **replace** the existing file — yes
3. Commit & push. No code change needed.

---

### Path B — GitHub Desktop + github.com (two tools)

**Always do this first:** open GitHub Desktop → click **Fetch origin** → if "Pull origin" appears, click it. This pulls down any code changes you made on the website so your local folder matches.

**Adding a new photo:**

*Step 1 — Add the file locally:*
1. Open your site folder (GitHub Desktop → Repository → Show in Finder/Explorer)
2. Open the **`Work`** folder
3. Drag your photo in
4. Rename it to start with the next number, e.g., `22 my-new-tattoo.jpg`

*Step 2 — Add the code line on github.com:*
1. Go to github.com/cweirdart/shervintattoo-site → click `index.html` → pencil icon
2. Search for `EDIT: GALLERY ITEMS`
3. Copy any existing gallery line, paste where you want it, change the filename — **replace spaces with `%20`**:

```
<div class="gallery-item" data-category="black-and-grey"><img src="Work/22%20my-new-tattoo.jpg" alt="Tattoo work by Shervin" loading="lazy"></div>
```

4. Set the category (see "Categories" below). Commit the change.

*Step 3 — Push the photo:*
1. Open GitHub Desktop → it shows the new photo in Changes
2. **Click Fetch origin first** (your code edit from Step 2 lives on the website; you need to pull it before pushing)
3. Click **Pull origin** when it appears
4. Type a summary ("added new tattoo photo") → **Commit to main** → **Push origin**

**Removing a photo:**
1. Delete the file from your `Work` folder
2. On github.com, edit `index.html`, delete the entire matching `<div class="gallery-item">...</div>` line. Commit.
3. In GitHub Desktop: Fetch → Pull → Commit the file deletion → Push.

**Replacing a photo (keep position, swap image):**
1. Drop the new file in your `Work` folder with the **same filename** as the old one (overwrite)
2. In GitHub Desktop: commit and push. No code change needed.

---

### Adding a video

Same steps as a photo, but the code line is slightly different:

```
<div class="gallery-item" data-category="black-and-grey"><video src="Work/22%20my-video.mp4" muted loop playsinline webkit-playsinline preload="auto"></video></div>
```

Keep videos under 3 MB — bigger videos can stutter on phones.

### Categories

Set the right `data-category` on each item:

- `"black-and-grey"` → Black and Grey tab
- `"color"` → Color tab
- `"flash"` → Flash tab
- `"color flash"` → both Color and Flash tabs (separated by a space)
- Remove `data-category="..."` entirely → only shows under "All"

### Reordering

Move the gallery-item lines up or down in `index.html`. Items display in the order they appear. The carousel automatically handles page breaks.

---

## Changing shop items

Search for `EDIT: SHOP` on github.com.

**Change a name:** Edit the text inside `<h3>...</h3>`

**Change a price:** Edit the text inside `<p class="price">...</p>`

**Add a product photo:**

1. **Name the file carefully:** use lowercase letters and hyphens, no spaces. E.g., `tiger-sketch.jpg`, NOT `Tiger Sketch.jpg`.
2. **Keep it under ~500 KB.** If your photo is bigger, ask any AI chat to resize it to 1600px wide (or use Mac Preview → Tools → Adjust Size).
3. **Add the file:** drag it into the **root folder** (NOT the `Work` folder — that's for the gallery only).
4. **In `index.html`, replace this line:**
   ```
   <div class="shop-item-image">Sold out</div>
   ```
   **with this** (keep the quotes around the filename, change just the two highlighted parts):
   ```
   <div class="shop-item-image"><img src="tiger-sketch.jpg" alt="Limited Edition Flash Sheet — tiger sketch"></div>
   ```
   - **`src="..."`** — your filename, in quotes. The quotes matter.
   - **`alt="..."`** — describe what's in the photo for accessibility and SEO.
5. Commit & push.

**Common mistakes to avoid:**
- ❌ `<img src=tiger sketch.jpg>` — missing quotes, and the space breaks everything
- ❌ `<img src="Tiger Sketch.jpg">` — spaces in filenames need `%20` (just rename the file with hyphens instead)
- ✅ `<img src="tiger-sketch.jpg" alt="...">` — clean and safe

---

## Shop & Payments — three ways to take an order

Each buy button can work in one of four modes. Pick whichever fits each product.

### Mode A — Sold Out (current default for all 4 items)

```
<button class="btn-buy sold-out" disabled>Sold Out</button>
```

Item stays visible on the site with line-through styling. No purchase possible.

### Mode B — Order form on the site → Venmo (no Stripe setup needed)

Customer clicks Buy → a modal pops up with an order form (name, email, address, qty) → customer submits → modal shows your Venmo handle + the exact amount + a unique memo string to use → customer pays via Venmo → you confirm payment in Venmo and ship.

```
<button class="btn-buy"
        data-checkout="open"
        data-product="Stoneware Vessel Vol. 1"
        data-price="120"
        data-payment-method="venmo"
        data-venmo-handle="@shervin510">Buy Now</button>
```

Set `data-product`, `data-price`, and `data-venmo-handle` for each item. The customer's order details email you automatically via Netlify Forms.

**Pros:** No Stripe verification wait. No fees on Venmo personal accounts. Personal touch. Works tonight.
**Cons:** Manual payment confirmation. Two-step UX (form → pay).

### Mode C — Order form on the site → Stripe checkout

Same as Mode B, but instead of showing Venmo instructions after the form submit, the modal shows a "Continue to Stripe" button.

```
<button class="btn-buy"
        data-checkout="open"
        data-product="DIASPORA Shirt"
        data-price="40"
        data-payment-method="stripe"
        data-stripe-link="https://buy.stripe.com/abcXYZ">Buy Now</button>
```

The order info is captured by Netlify Forms BEFORE the Stripe checkout, so you have the customer's address and notes even if they abandon the Stripe checkout.

**Pros:** Polished Stripe checkout for payment. Order info captured before payment. Hybrid.
**Cons:** Requires Stripe account. Two-step UX.

### Mode D — Direct to Stripe (no on-site form)

Cleanest one-click flow — customer clicks Buy and goes straight to Stripe checkout. Stripe collects email and shipping address.

```
<a href="https://buy.stripe.com/abcXYZ" target="_blank" rel="noopener" class="btn-buy">Buy Now</a>
```

**Pros:** Single click, single page. Polished. Stripe handles everything.
**Cons:** Requires Stripe account verified (1-2 day wait). No site-side capture (you only see orders that actually paid).

---

## Setting up Stripe (only needed for Modes C and D)

You only do this once, ever:

1. Sign up at **https://stripe.com** with the email you want on receipts
2. Complete identity verification — needs your legal name, last 4 of SSN, home address (~1-2 business days to verify)
3. Link your bank account — routing + account number for payouts
4. Set your business display name (what customers see at checkout)

### To create a Stripe Payment Link

1. **In Stripe Dashboard** → **Products** → **+ Add Product**
   - Name, price, photo
   - Enable **"Collect shipping address"** (for physical items)
   - Configure shipping rates and regions (US-only or international)
   - Set quantity limit if it's a limited edition
2. Click **"Create Payment Link"** for that product
3. Copy the URL — looks like `https://buy.stripe.com/abcXYZ123`
4. Paste it into the buy button — see Mode C or Mode D above

---

## Setting up Venmo (only needed for Mode B)

If you don't already have one, create a Venmo account at https://venmo.com. For low volume (under ~$500/month), a **personal** Venmo account is fine and has no fees. Once volume grows, switch to a **business** account (1.9% + $0.10 per transaction).

Shervin's current Venmo handle: **`@shervin510`** — this is what gets pasted into the `data-venmo-handle` attribute on each buy button.

### Per-order Venmo flow (what happens on Shervin's side)

1. Customer fills the order form on the site
2. Netlify emails you: name, email, shipping address, item, order ID
3. Customer pays you Venmo with memo `ORD-XXXXX` (matches the order ID)
4. You match the Venmo payment to the order email
5. You reply to the customer confirming the order and a rough ship date
6. You ship; ideally include the order ID on the packing slip

---

## Where do orders show up?

- **Modes B + C:** Netlify Forms emails you (via the project's notifications) with name + email + shipping address + product + order ID. Customer also gets an auto-reply confirming order received.
- **Mode D (Stripe direct):** Stripe emails you when payment lands. Customer gets Stripe's receipt.
- **All modes:** check Netlify Forms dashboard for backup history of submissions.

## Stripe-side details worth knowing

- **Fees:** 2.9% + 30¢ per transaction. On a $100 sale you net ~$96.60.
- **Payouts:** Stripe transfers the balance to your bank on a rolling 2-day schedule by default. Adjustable in Stripe settings.
- **Inventory limits:** set a quantity cap when creating a product. Customers see "no longer available" once the cap is hit. Best paired with marking the item Sold Out on the site too.
- **Tax:** **Stripe Tax** auto-calculates US state sales tax if you enable it. Worth doing for California sellers (state law).
- **Refund policy:** Stripe requires you to have one for physical goods. A draft is in `REFUND-POLICY.md` in this repo — review it with c.weird before publishing.
- **Test mode:** Stripe gives you both test and live mode. Use test mode (with test card numbers) to verify the full flow before going live.

---

## Adding a new filter category

1. Search for `EDIT: FILTER BUTTONS` and add a button:
```
<button data-filter="japanese">Japanese</button>
```

2. On each gallery item in that category, set `data-category="japanese"`

The filter value on the button must exactly match the category value on the items.

---

## The one rule (only if you're using GitHub Desktop): Fetch before local changes

This rule only applies to **Path B (Desktop + web editor)**. If you do everything in github.dev (Path A), skip this section — there's no local folder, so nothing to sync.

If you're on Path B and you edited code on github.com and then want to add photos locally, **always open GitHub Desktop and click Fetch origin first**. This syncs your local folder with what's on the website. If you skip this, you might get a conflict error. If that happens, it's fixable — but easier to just Fetch first every time.

**The simplest way to never hit this issue:** switch to Path A (github.dev). One tool, one place, no sync.

---

## If something breaks

Nothing is ever permanently lost. Every version is in git history. Here's how to roll back to the last working version:

**Easiest — Undo on github.com:**

1. Go to github.com/cweirdart/shervintattoo-site
2. Click **Commits** (near the top of the file list)
3. Find the commit you want to undo (usually the most recent one)
4. Click the commit message → look for the **... (3-dot menu)** → click **Revert**
5. This opens a Pull Request — click **Create pull request** → then **Merge pull request**
6. Site rebuilds within 60 seconds with the bad change undone

**In GitHub Desktop (Path B only):**

1. Go to the **History** tab (left sidebar)
2. Right-click the bad commit
3. Click **Revert Changes in Commit**
4. Push

**When in doubt, text c.weird** at info@cweird.com — better to ask than to keep poking at it.

---

## Optional: Using AI for help

You don't need any AI tool to edit this site. But if you're stuck on how to write a specific line of HTML, AI can write or rewrite it for you.

### For one-off help (free, no setup)

Open **claude.ai** or **chatgpt.com** in another tab. Paste the line you want to change and describe what you want:

> "I have this gallery line. How do I change it so it points to a file called `23 dragon-sleeve.jpg` and shows under the Color filter?"
>
> ```html
> <div class="gallery-item" data-category="black-and-grey"><img src="Work/22%20old-tattoo.jpg" alt="Tattoo work by Shervin" loading="lazy"></div>
> ```

Copy the answer back into github.dev or github.com, save, commit.

### For bigger edits (also free, deeper integration)

These tools can read the whole repo and make multi-line changes:

- **[ChatGPT Codex](https://chatgpt.com/codex)** — free, connects to your GitHub repo and can edit + commit for you. Probably the easiest paid-equivalent that's free.
- **[Gemini CLI](https://github.com/google-gemini/gemini-cli)** — free with a Google account, generous quota, runs in your Terminal.
- **[Claude Code](https://claude.com/claude-code)** — most polished but requires a Claude Pro subscription ($20/mo) or pay-per-use API credit (~15-30¢ per session).
- **[Cursor](https://cursor.com)** — a code editor with AI built in. Has a free tier.

For the rare-edit volume you'll have, the free options are plenty.

---

## Don't touch these

- Everything in the `<script>` section at the bottom of the file
- The `cf-turnstile` line (spam protection)
- `data-netlify="true"` on the booking form
- The `_redirects` file

If you need changes to any of these, ask c.weird.

---

## Costs

| Service | What it does | Cost |
|---|---|---|
| Netlify | Hosts the website | $9/month |
| GitHub | Stores the code | Free |
| Cloudflare Turnstile | Blocks spam on the booking form | Free |
| Namecheap | Domain name (shervintattoo.com) | ~$12/year |

Your domain auto-renews through Namecheap. Make sure the payment method stays current at [namecheap.com](https://ap.www.namecheap.com).

---

## File map

```
shervintattoo-site/
├── index.html              ← The whole website (this is what you edit)
├── Work/                   ← Gallery photos and videos
├── hero-video.mp4          ← Background video on the homepage
├── Shervin_Polaroid_bycweird.jpeg
├── Shervin_businesscard_1.jpg
├── Shervin_businesscard_2.jpg
├── TattooingByServin_logo+flowers.png
├── og-image.jpg            ← Preview image when shared on social media
└── (other files — don't touch)
```

---

## Need help?

Reach out to c.weird at info@cweird.com for:

- Redesigns or new sections
- Domain or DNS issues
- Anything that feels risky
- Anything at all — better to ask than to guess
