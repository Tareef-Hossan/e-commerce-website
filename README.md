# E-commerce-website
I've now gone through both the frontend site and its backend. Here's a description:

## A full-stack streetwear/fashion e-commerce site

This is a much more elaborate build than the earlier "Get Protected" cybersecurity site — a complete clothing-brand storefront with a real backend, not just a static page.

**Brand & design**
- Name: **Theory Archive**, styled as a limited-drop streetwear label ("released once, in a fixed quantity, and never remade — when it's gone, it moves to the Archive for good")
- Dark, editorial aesthetic — black background, serif display headings (Playfair Display) paired with a grotesque sans (Manrope), pill-shaped buttons, glitch-text hero, marquee ticker, scroll-reveal animations

**Frontend (`theory-site/index.html`, ~2,570 lines, single file)**
- Sections: hero → marquee → **New Arrivals** (product grid) → **Field Notes** (brand/vision copy) → **Field Reports** (customer reviews, star ratings) → footer
- 9 products shown (e.g. Structured Collapse Blazer $600, Weighted Field Coat $540, Reinforced Utility Hood $310, Archive Balaclava $85), each with a quick-view product modal, size selector (XS–XL), image gallery, and an "Add to Bag" flow
- Shopping cart drawer + full **checkout modal**: shipping address, shipping-method options, a promo/coupon code field, and payment method selection including **PayPal**
- Sign up / log in **auth modal** with email+password fields and social-login buttons (styled placeholders)
- `admin.html` — a separate, `noindex` back-office page for managing **products & stock** (stock levels, low/out-of-stock badges, add-product form, review moderation)

**Backend (`theory-archive-auth-backend/`, Node.js/Express)**
- A real authentication API: `bcryptjs` password hashing, JWT access tokens + rotating single-use refresh tokens (both `httpOnly` cookies), rate-limited login, `better-sqlite3` for storage, `nodemailer` for email
- Routes for `auth`, `products`, `orders`, `coupons`, and `reviews`
- Ships with a `README.md` explaining setup, a `seed.js` script, a `backup.js` script, and a `.env.example` — plus an actual `.env` file was included in the zip (worth swapping out real secrets before deploying, if any are live in there)

So structurally: static/vanilla-JS frontend (no framework, no build step) talking to a small dedicated Express+SQLite auth/commerce backend — a more "real" e-commerce stack than a typical template.
