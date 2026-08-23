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

## 4. Turn on email alerts for new project briefs

The "Start your project" form on your site is wired to **Netlify Forms** — every submission is captured automatically once the site is live (no extra setup needed for that part). To get an email every time someone submits:

1. In your Netlify site dashboard, go to **Forms** (left sidebar).
2. You should see a form called **project-brief** listed once your first real submission comes in, or immediately after your first deploy.
3. Go to **Site configuration → Forms → Form notifications** → **Add notification** → **Email notification**.
4. Enter the email address you want briefs sent to, save.

From then on, every submission both shows up in the **Forms** tab in Netlify and lands in your inbox. If you ever want submissions to go straight to WhatsApp instead of/alongside email, let me know — that needs a small extra integration (e.g. Zapier or a webhook), which I can set up.

## 6. Newsletter signup

There's now a "Get new work in your inbox" signup band right above the footer. It works the same way as your project-brief form — submissions are captured for free via Netlify Forms.

1. Follow the same steps as section 4 above, but this time turn on a notification for the **newsletter-signup** form (Site configuration → Forms → Form notifications → Add notification → Email notification).
2. That's enough to start collecting subscribers today, at zero cost.

### Upgrading to real email campaigns (Mailchimp, free)

Netlify Forms only *collects* emails — it can't send newsletters. When you're ready to actually email your subscribers:

1. Sign up free at [mailchimp.com](https://mailchimp.com) (free plan covers up to 500 contacts).
2. Create an **Audience** (Mailchimp's term for a mailing list).
3. Go to Audience → Signup forms → Embedded forms, and copy the form's **action URL** (looks like `https://yourname.usX.list-manage.com/subscribe/post?u=...&id=...`).
4. Send me that URL and I'll switch the newsletter form on your site to submit directly into Mailchimp instead of Netlify — from then on, new signups appear straight in your Mailchimp audience, ready for you to design and send a campaign to whenever you want.
5. Alternatively, periodically export your collected emails from Netlify Forms (Download as CSV) and import them into Mailchimp manually.

Either way, actually **writing and sending** a newsletter is still something a person (or you asking me to help draft one) needs to do — no tool sends itself.

## 7. Editing videos, contact info, and text later
Just log into `/admin`, make changes, click **Publish**. That's it — you never need to touch GitHub or code again for text/video/contact updates. For bigger layout or design changes, come back and ask for those directly.
