# The Creative Bulb — Website

## What's in this repo

```
index.html          → the website
assets/logo.webp     → your logo
assets/favicon.png   → browser tab icon
content/data.json    → editable text/contact/video content (the admin panel edits this file)
admin/               → your content admin panel (Decap CMS)
netlify.toml         → security headers + hosting config
```

## 1. Push to GitHub, deploy to Netlify

Follow the same steps as before — create a GitHub repo, upload all these files (keep the folder structure exactly as-is), then import that repo into Netlify. No build command needed; publish directory is `.`.

## 2. Turn on your admin panel (total control, no code)

This gives you a private login page at **yoursite.com/admin** where you can edit headline text, contact info, YouTube videos, about text, and swap the logo — no code, no developer needed. Every save automatically updates the live site within about a minute.

1. In your Netlify site dashboard, go to **Site configuration → Identity** and click **Enable Identity**.
2. Under Identity → **Registration**, set it to **Invite only** (important — this stops strangers from signing up as editors).
3. Under Identity → **Services**, enable **Git Gateway**.
4. Go to the **Identity** tab (top nav of your site in Netlify) → **Invite users** → enter your own email. You'll get an email to set a password.
5. Visit `yoursite.com/admin`, log in, and you'll see an editor for every section of the site.

## 3. Security — what's already in place

- **No database, no server, no login forms exposed to the public** — this is a static site, which removes almost the entire attack surface a "hacked website" usually has (no SQL injection, no server exploits, no exposed admin database).
- **Security headers** are set in `netlify.toml` (clickjacking protection, MIME-sniffing protection, and a Content-Security-Policy restricting what scripts can run on your site).
- **HTTPS is automatic and free** on Netlify.
- **The `/admin` editor is invite-only** — only people you explicitly invite via Netlify Identity can log in and change content. Random visitors cannot reach it.

### What you should still do
- Turn on **2-Factor Authentication** on both your GitHub and Netlify accounts (Settings → Password and Authentication).
- Never share your Netlify Identity invite or GitHub login with anyone you don't fully trust — whoever holds that login has full editing/control rights.
- Only invite editors you personally trust; remove access (Identity → user → Delete) for anyone who no longer needs it.

## 4. Editing videos, contact info, and text later
Just log into `/admin`, make changes, click **Publish**. That's it — you never need to touch GitHub or code again for text/video/contact updates. For bigger layout or design changes, come back and ask for those directly.
