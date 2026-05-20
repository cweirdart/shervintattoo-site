# Shervin Tattoo — Site Owner's Guide

Welcome. This is your website's source code and instructions for editing it yourself. The live site is at **https://shervintattoo.com** and is hosted by Netlify.

Built and handed off by **c.weird** (info@cweird.com).

You don't need to be a developer to edit this site — you just need Claude Code (or any other LLM editor) and the prompts below.

---

## How this works at a glance

```
You edit on your laptop  →  Push to GitHub  →  Netlify auto-deploys  →  shervintattoo.com updates
```

You never type a single line of code or git command yourself. **Claude Code does all of that.** You just describe what you want changed in plain English.

---

## One-time setup (do this once on your laptop)

You'll need:

1. **GitHub** — you already have an account and a collaborator invite from Christopher. Accept the invite if you haven't yet (check your GitHub notifications or your email).
2. **Claude Code** — install from https://claude.com/claude-code. Sign in with your Anthropic account (Claude Pro/Max covers it, or you can pay per-use with an API key).
3. **Git** — already installed on Mac. On Windows, install from https://git-scm.com.

Once those are set up, open Terminal (Mac) or PowerShell (Windows) and run:

```bash
cd ~/Documents
git clone https://github.com/cweirdart/shervintattoo-site.git
cd shervintattoo-site
claude
```

That last `claude` command opens Claude Code in this folder. From now on, that's where you do all your editing.

---

## How to make any change

1. Open Terminal
2. Navigate to the project: `cd ~/Documents/shervintattoo-site`
3. Run `claude` to start Claude Code
4. **Tell Claude what you want changed.** Examples below.
5. Claude makes the edit, shows you the changes, and asks for permission to commit + push.
6. Once you say yes, Netlify auto-deploys within ~30-60 seconds.
7. Visit shervintattoo.com to see it live.

That's the whole workflow.

---

## Common tasks — copy and paste these prompts

### Update a shop item price

> Change the price of the Stoneware Vessel Vol. 1 in the Shop section from $120 to $130.

### Mark a shop item back in stock (or sold out)

> Mark the DIASPORA Limited Edition Shirt as in stock. Remove the "Sold Out" badge and change the button to a real "Buy Now" link.

### Update business location / address

> Change the studio address in the About section from "1038 Larkin St, San Francisco" to "<new address>". Update both the visible text and the structured-data JSON-LD block at the top of index.html.

### Add a new tattoo to the gallery

> I want to add a new tattoo photo to the gallery. The image is saved at Work/20.jpg. It's a black and grey piece. Add it as the next gallery item.

(Save the photo into the `Work/` folder first, then run the prompt.)

### Remove a photo from the gallery

> Remove the gallery item that uses Work/3 Shervin_tattooing_byextraekster.jpg.

### Update the About paragraph

> Rewrite the second paragraph in the About section to say: "Currently taking appointments at <new studio name> — <new address>, <new days>."

### Add a new style to the form's "Style of tattoo" dropdown

> In the booking form's "Style of tattoo" dropdown, add a new option called "Geometric" between "Ornamental" and "Other".

### Update the Instagram handle

> Change the Instagram link everywhere on the site from shervin.510 to <new-handle>.

### Update contact email

> Change the contact email throughout the site from shervinx510@gmail.com to <new email>.

---

## Adding or replacing photos

1. Put the photo file in the `Work/` folder if it's a tattoo, or in the root folder if it's a different kind of image (portrait, logo, etc.).
2. **Important:** keep photos under 2 MB. If it's larger, ask Claude to resize it:

   > Resize Work/<your-filename>.jpg to 1600 pixels wide and recompress it.

3. Then ask Claude to add it to the gallery (see prompt above).

**Why this matters:** older iPhones can't load very large photos. Keeping images at or below 1600px wide ensures everyone can see them.

---

## "Uh oh — something looks broken on the live site"

Don't panic. Every change is in git history, which means it's easy to roll back. Just tell Claude:

> The last change broke something. Roll back the last commit and push.

If multiple changes are bad:

> Show me the last 5 commits with their dates and descriptions.

Then:

> Roll back to the commit before <description of last good state> and push.

If everything goes sideways and you want help, **call Christopher.** Don't keep prompting if it feels wrong — text c.weird at info@cweird.com.

---

## Where things live

```
shervintattoo-site/
├── index.html              ← The entire website lives in this one file
├── ONBOARDING.md           ← This guide
├── _redirects              ← Netlify URL redirects (rarely touched)
├── llms.txt                ← Metadata for AI crawlers
├── STYLE-GUIDE.md          ← Visual brand notes
├── Work/                   ← All tattoo gallery photos and videos
├── hero-video.mp4          ← The video that plays at the top of the homepage
├── Shervin_Polaroid_bycweird.jpeg  ← Portrait photo
├── Shervin_businesscard_*.jpg      ← Business card front + back
├── TattooingByServin_logo+flowers.png  ← The stylized hero logo
├── shervin-pomegranate.png ← Email illustration in contact section
├── shervin-skull.png       ← Instagram illustration in contact section
└── og-image.jpg            ← The preview image when the site is shared on social
```

You almost never need to know any of this — Claude figures it out. But if you ever want to read or change `index.html` directly, that's the only file you'd need.

---

## Anti-spam (already set up)

Your booking form is protected against spam by four layers:
1. Netlify's built-in honeypot
2. A secondary honeypot in the form HTML
3. A 3-second minimum form-fill timer
4. **Cloudflare Turnstile** — an invisible CAPTCHA (free, runs in the background)

If spam ever starts getting through again, ask Claude:

> Spam is getting through the booking form. Investigate and propose fixes.

The Cloudflare Turnstile dashboard is at https://dash.cloudflare.com/ → Turnstile.

---

## Hosting + cost overview

| Service | Used for | Cost |
|---|---|---|
| **Netlify** | Hosting shervintattoo.com | Free tier |
| **GitHub** | Storing the code, version history | Free |
| **Cloudflare Turnstile** | Spam protection | Free |
| **Claude Code** | LLM editor | Covered by Claude Pro ($20/mo) or pay-per-use via API |

Total: $0 to $20/month depending on how you pay for Claude.

---

## Domain renewal

`shervintattoo.com` is registered in your name with **Namecheap**. It auto-renews annually. If renewal fails, the site goes offline — make sure the credit card on your Namecheap account stays current. Log in at https://ap.www.namecheap.com to check.

---

## When to call Christopher (c.weird)

Most edits you can handle yourself with Claude. Call/text Christopher (info@cweird.com) for:

- Big visual redesigns
- Adding entirely new sections or pages
- Anything to do with the domain, DNS, or Cloudflare
- The site is broken and rolling back didn't fix it
- Anything you're not sure about — better to ask than to push something wrong

---

## One small thing to remember

Every time Claude pushes a commit, Netlify rebuilds the site. This takes about **30-60 seconds**. If you don't see your change immediately, give it a minute and refresh. If it's been more than 2-3 minutes, log into https://app.netlify.com and check the "Deploys" tab for errors.

---

Have fun. The site is yours. ❤️

— c.weird
