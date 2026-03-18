# No Sweat Bets Landing Page

Static landing page for **No Sweat Bets (NSB)** – a private sports betting Discord community. The page is built as a single, deploy-ready HTML/CSS site that works well on Vercel or Netlify.

## Structure

Project folder: `nsb-landing/`

- `index.html` – Main landing page markup
  - **Hero**
    - Headline and subheading aimed at serious sports bettors
    - Primary CTA: **Join the Discord** (links to the NSB Discord invite)
    - Secondary CTA: **View Membership Options** (links to the Whop page)
    - Social icons/links for Instagram and Twitter/X
    - Side card that mimics a betting "slip" with example entries (purely visual)
  - **What You Get** (`#about`)
    - Four feature cards: Daily picks, Live bets, Bankroll education, Community
  - **Plans / Membership** (`#plans`)
    - Three plan cards: Monthly Access, Season Pass, VIP All-Access
    - No hardcoded prices; all CTAs point to the NSB Whop checkout
  - **Social Proof / Testimonials** (`#testimonials`)
    - Four testimonial blocks with realistic but generic placeholder copy
  - **FAQ** (`#faq`)
    - 6 questions/answers:
      - What NSB is
      - How picks are delivered
      - Bankroll expectations
      - Refund policy
      - Disclaimer re: financial advice / guarantees
      - Cancellation via Whop
  - **Footer**
    - Links to Instagram, Twitter/X, Discord, and Whop
    - Gambling risk disclaimer and 18+/21+ legal age note
    - Auto-updating copyright year via a tiny inline script
- `styles.css` – All styles for the page
  - Dark theme background with subtle neon green glow
  - Accent color: **#00FF41**-ish neon green
  - Clean, modern typography using **Inter** via Google Fonts
  - Responsive layout using CSS Grid and flexbox, no JS frameworks

There are **no build steps** and **no external dependencies** beyond Google Fonts. It&apos;s just HTML + CSS.

## Local Preview

You can open `nsb-landing/index.html` directly in a browser to preview:

1. From Finder or your file explorer, open the `nsb-landing` folder.
2. Double-click `index.html` to open it in your default browser.

For better local dev (avoids some browser security restrictions and lets you share URLs on localhost), you can run any simple static server, e.g.:

```bash
cd nsb-landing
python -m http.server 8000
# then visit http://localhost:8000 in your browser
```

## Deploying to Vercel (no CLI)

These instructions assume the landing page is in a GitHub repo. You can either:

- Put `nsb-landing/` at the **root** of its own repo, or
- Keep it as a **subfolder** in a larger repo and point Vercel at that folder.

### 1. Push to GitHub

1. Create a new GitHub repo (e.g. `nsb-landing`).
2. From your local machine:

   ```bash
   cd /Users/kevinfritz/.openclaw/workspace
   # if this folder isn&apos;t already the repo root, `cd` into the correct repo first
   git status
   git add nsb-landing
   git commit -m "NSB: initial landing page"  # if not already committed
   git push origin main                        # or whatever your main branch is
   ```

### 2. Create a Vercel project via the dashboard

1. Go to **https://vercel.com/** and log in.
2. Click **Add New... → Project**.
3. Choose **Import Git Repository** and select the repo that contains `nsb-landing`.
4. Configure the project:
   - If the repo only contains this landing page and `index.html` is at the root:
     - **Framework Preset**: `Other`
     - **Root Directory**: `/` (leave blank in the UI)
     - **Build Command**: leave empty
     - **Output Directory**: `.`
   - If the repo has multiple projects and this is in `nsb-landing/`:
     - After selecting the repo, click **Edit** next to project settings.
     - Set **Root Directory** to `nsb-landing`.
     - **Framework Preset**: `Other`
     - **Build Command**: leave empty
     - **Output Directory**: `.` (Vercel will serve `index.html` inside that root folder)
5. Click **Deploy**.

Vercel will detect there&apos;s no build step and serve the static files directly. Once the deploy finishes, you&apos;ll get a live URL (and you can later add a custom domain).

## Deploying to Netlify (no CLI)

Again, start from the repo that contains `nsb-landing/`.

### 1. Connect the repo

1. Go to **https://app.netlify.com/** and log in.
2. Click **Add new site → Import an existing project**.
3. Choose **GitHub** and pick the repo with your landing page.

### 2. Configure the site

- If `nsb-landing` is the root of the repo:
  - **Build command**: leave blank (or `none`)
  - **Publish directory**: `.`
- If `nsb-landing` is a subfolder in a larger repo:
  - Click **Show advanced** (or similar) to set the base directory.
  - **Base directory**: `nsb-landing`
  - **Build command**: leave blank
  - **Publish directory**: `.` (relative to that base directory)

Click **Deploy site**.

Netlify will upload and serve `index.html` and `styles.css` as-is. After the first deploy, any push to the configured branch will auto-trigger a redeploy.

## Editing the Page

The main sections in `index.html` are clearly labeled with comments and IDs:

- `#hero` – headline, CTAs, side slip panel, and social icons
- `#about` – "What you get" feature cards
- `#plans` – membership cards and CTAs to Whop
- `#testimonials` – four testimonial blocks
- `#faq` – FAQ accordion
- Footer – social links and disclaimers

Most styling is controlled by classes in `styles.css`:

- Layout & spacing: `.section`, `.container`, `.hero-inner`, `.plans-grid`, `.testimonials-grid`, `.faq-grid`, `.footer-inner`
- Buttons: `.btn`, `.btn-primary`, `.btn-outline`, `.btn-ghost`, `.btn-accent`, `.btn-lg`, `.btn-block`
- Cards: `.feature-card`, `.plan-card`, `.testimonial-card`, `.faq-item`, `.hero-panel-card`
- Text & badges: `.hero-tagline`, `.hero-meta-item`, `.plan-label`, `.pill`, `.hero-meta-label`, `.testimonial-name`, `.testimonial-meta`

To tweak branding:

- Adjust colors in `styles.css` under the `:root` CSS variables (especially `--accent`, `--bg`, `--bg-elevated`).
- Update fonts by changing the Google Fonts link in `index.html` and the `font-family` in `body`.
- Swap social URLs in both the hero section and the footer once you have the final profiles.

No additional build tools are required – edit the files, commit, and push to redeploy.
