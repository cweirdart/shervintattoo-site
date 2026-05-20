# How to Edit Your Website

**Site:** https://shervintattoo.com
**Repo:** https://github.com/cweirdart/shervintattoo-site
**Built by:** c.weird (info@cweird.com)

---

## How it works

Your website is one file: `index.html`. It lives on GitHub. Every time you make a change and save it, Netlify automatically updates the live site within about 60 seconds.

You'll use two tools (both free):

- **github.com** (in your browser) — for editing text, prices, gallery code, etc.
- **GitHub Desktop** (app on your computer) — for adding, replacing, or deleting photos and videos

---

## Setup (one time only)

You've already done this:

1. ✅ GitHub account created
2. ✅ Collaborator invite accepted
3. ✅ GitHub Desktop installed
4. ✅ Repository cloned to your computer

Your site files are now in a folder on your computer. To find it: open GitHub Desktop → **Repository → Show in Finder** (Mac) or **Show in Explorer** (Windows).

---

## Editing text, prices, or code

Do this on github.com in your browser.

1. Go to **github.com/cweirdart/shervintattoo-site**
2. Click on **index.html**
3. Click the **pencil icon** (top right of the file) to edit
4. Press **Cmd+F** (Mac) or **Ctrl+F** (Windows) and search for **EDIT:** to jump between editable sections
5. Make your changes
6. Click **Commit changes** (green button, top right)
7. Add a short note about what you changed (e.g., "updated flash sheet price")
8. Click **Commit changes** again to confirm
9. Wait about 60 seconds, then refresh shervintattoo.com — your change is live

That's it.

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

**One rule:** If you need an **&** symbol, type `&amp;` instead (e.g., `Black &amp; Grey`).

---

## Adding or removing photos and videos

Do this in GitHub Desktop + your local folder.

### Before you start: always sync first

Open GitHub Desktop and click **Fetch origin** (top bar). If it says **Pull origin** after that, click it too. This makes sure your local files are up to date with any changes you made on the website.

### Adding a new photo to the gallery

**Step 1 — Add the file:**

1. Open your site folder on your computer (GitHub Desktop → Repository → Show in Finder/Explorer)
2. Open the **Work** folder
3. Drag your new photo in
4. Name it with a number prefix, like `22 my-new-tattoo.jpg` — the number controls the order

**Step 2 — Add the code line:**

1. Go to **github.com/cweirdart/shervintattoo-site** → click **index.html** → pencil icon
2. Search for `EDIT: GALLERY ITEMS`
3. Copy one of the existing gallery lines and paste it where you want the new image
4. Change the filename — **replace spaces with `%20`**:

```
<div class="gallery-item" data-category="black-and-grey"><img src="Work/22%20my-new-tattoo.jpg" alt="Tattoo work by Shervin" loading="lazy"></div>
```

5. Set the category:
   - `"black-and-grey"` → Black and Grey tab
   - `"color"` → Color tab
   - `"flash"` → Flash tab
   - `"color flash"` → both Color and Flash tabs
   - Remove `data-category="..."` entirely → only shows under All
6. Commit the change on GitHub

**Step 3 — Push the photo:**

1. Open GitHub Desktop — it will show the new photo file in the Changes tab
2. Type a summary (e.g., "added new tattoo photo")
3. Click **Commit to main**
4. Click **Push origin**

Both the code change and the new photo are now live.

### Adding a video

Same steps, but use this code line instead:

```
<div class="gallery-item" data-category="black-and-grey"><video src="Work/22%20my-video.mp4" muted loop playsinline webkit-playsinline preload="auto"></video></div>
```

### Removing a photo or video

1. Delete the file from the `Work` folder on your computer
2. On github.com, edit `index.html` and delete the entire line for that item (the whole `<div class="gallery-item">...</div>`)
3. Commit on github.com
4. In GitHub Desktop: commit the file deletion, then push

### Replacing a photo

If you want to swap a photo but keep it in the same gallery position:

1. Put the new file in the `Work` folder with the **same filename** as the old one (overwrite it)
2. In GitHub Desktop: commit and push
3. No code changes needed — the HTML already points to that filename

### Reordering

Move the gallery-item lines up or down in the code on github.com. Items display in the order they appear. The carousel automatically handles page breaks.

---

## Changing shop items

Search for `EDIT: SHOP` on github.com.

**Change a name:** Edit the text inside `<h3>...</h3>`

**Change a price:** Edit the text inside `<p class="price">...</p>`

**Mark as available:** Change the button from:
```
<button class="btn-buy sold-out" disabled>Sold Out</button>
```
To:
```
<button class="btn-buy">Add to Cart</button>
```

**Mark as sold out:** Change the button from:
```
<button class="btn-buy">Add to Cart</button>
```
To:
```
<button class="btn-buy sold-out" disabled>Sold Out</button>
```

**Add a product photo:** Replace:
```
<div class="shop-item-image">Sold out</div>
```
With:
```
<div class="shop-item-image"><img src="your-photo.jpg" alt="Product name"></div>
```
Then add the photo file through GitHub Desktop (same as gallery photos, but put it in the main folder, not `Work`).

---

## Adding a new filter category

1. Search for `EDIT: FILTER BUTTONS` and add a button:
```
<button data-filter="japanese">Japanese</button>
```

2. On each gallery item in that category, set `data-category="japanese"`

The filter value on the button must exactly match the category value on the items.

---

## The one rule: Fetch before local changes

If you edited code on github.com and then want to add photos locally, **always open GitHub Desktop and click Fetch origin first**. This syncs your local folder with what's on the website. If you skip this, you might get a conflict error. If that happens, it's fixable — but easier to just Fetch first every time.

---

## If something breaks

**Option 1 — Undo on github.com:**

1. Go to github.com/cweirdart/shervintattoo-site
2. Click **Commits** (near the top)
3. Find the commit that broke things
4. Click it → click **Revert** (or ask c.weird for help)

**Option 2 — Undo in GitHub Desktop:**

1. Go to the **History** tab
2. Right-click the bad commit
3. Click **Revert Changes in Commit**
4. Push

Nothing is ever permanently lost. Git keeps every version.

---

## Optional: Using AI for help

You don't need any AI tool to edit this site. But if you're stuck on how to write a specific line of HTML, you can paste the line into any free AI chat (Claude, ChatGPT, whatever) and ask. For example:

> "I have this gallery line. How do I change it to point to a file called 23 dragon-sleeve.jpg in the color category?"

For bigger edits, [ChatGPT Codex](https://chatgpt.com/codex) (free) can connect to your GitHub repo and make code changes directly. [Claude Code](https://claude.com/claude-code) and [Cursor](https://cursor.com) are other options but require paid plans or local setup.

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
