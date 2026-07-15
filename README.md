# City Capital — Booking & Thank-You Pages

Two static pages for citycapital.ca:

- `index.html` — booking page with a **Calendly inline embed**
- `thank-you.html` — post-booking page explaining what happens next
- `styles.css` — shared brand styles (all colors defined at the top as CSS variables)

No build step. Pure HTML/CSS/JS. Deploys to Vercel as-is.

---

## 1. Set your Calendly link (required before going live)

Open `index.html` and find the Calendly embed near the middle:

```html
<div class="calendly-inline-widget"
     data-url="https://calendly.com/YOUR-CALENDLY-USERNAME/funding-call?hide_gdpr_banner=1&primary_color=f4b942"
     ...>
```

Replace `YOUR-CALENDLY-USERNAME/funding-call` with your real Calendly event URL.

### Redirect to the thank-you page after booking
In Calendly: open the event type → **Confirmation page** → **Redirect to an external site** →
paste your live URL + `/thank-you` (e.g. `https://citycapital-booking.vercel.app/thank-you`).
That way every booking lands on the thank-you page automatically.

---

## 2. Match the exact brand colors (optional)

All colors live at the top of `styles.css` under `:root`. Change these hex values and both
pages update instantly:

```css
--navy: #0B2545;   /* primary */
--gold: #F4B942;   /* accent / buttons */
```

---

## 3. Deploy to Vercel

### Option A — via GitHub (recommended, auto-deploys on every push)
1. Create a new repo on GitHub (e.g. `citycapital-booking`).
2. Push this folder:
   ```bash
   git init
   git add .
   git commit -m "City Capital booking + thank-you pages"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/citycapital-booking.git
   git push -u origin main
   ```
3. Go to https://vercel.com/new → Import the repo → **Deploy** (no settings needed; it's static).
4. Vercel gives you a live URL. Add a custom domain/subdomain under **Settings → Domains**
   (e.g. `book.citycapital.ca` via a CNAME record).

### Option B — Vercel CLI (no GitHub)
```bash
npm i -g vercel
vercel        # first run links/creates the project
vercel --prod # deploy to production
```

---

## Custom subdomain (e.g. book.citycapital.ca)
In Vercel → Project → Settings → Domains → add `book.citycapital.ca`, then add the CNAME
record Vercel shows you at your DNS provider.
