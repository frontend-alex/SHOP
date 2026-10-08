# SHOP

A single-repository Next.js online-store prototype with catalog browsing, cart UI, Google sign-in, and Stripe checkout code.

## Current status

Learning prototype. Payment and order behavior should be treated as unfinished integrations rather than verified commerce features.

## Features and implementation

- Catalog and item-detail pages, a cart page, and account/settings screens.
- Next.js API routes for catalog and profile data backed by MongoDB.
- Google authentication through NextAuth.
- A payment route that attempts to create a Stripe checkout session.

## Technology

Next.js, React, JavaScript, MongoDB/Mongoose, NextAuth, Stripe, and Tailwind CSS.

## Repository map

| Path | Purpose |
| --- | --- |
| [src/app](<src/app>) | Store pages and route handlers |
| [src/app/api/catalog](<src/app/api/catalog>) | Catalog endpoints |
| [src/app/api/payment/route.js](<src/app/api/payment/route.js>) | Checkout-session prototype |
| [src/app/api/auth](<src/app/api/auth>) | Google sign-in configuration |
| [src/lib/db.js](<src/lib/db.js>) | MongoDB connection |

## Local setup

```bash
git clone https://github.com/frontend-alex/SHOP.git
cd SHOP
npm install
```

Before starting, create .env.local with your own values:

```dotenv
MONGODB_URL=mongodb://127.0.0.1:27017/shop_local
GOOGLE_ID=replace-with-your-client-id
GOOGLE_CLIENT_SECRET=replace-with-your-client-secret
STRIPE_PRICE_KEY=replace-with-your-stripe-test-secret-key
```

Despite its name, STRIPE_PRICE_KEY is passed to the Stripe client as an API secret key, not a product price ID. Review provider callback configuration and use Stripe test mode when reviewing the checkout code. Open http://localhost:3000.


Start the development server after configuration:

```bash
npm run dev
```

## Verification

The manifest provides the following checks:

```bash
npm run lint
npm run build
```

These commands were checked against the manifest; builds, browser flows, and external services were not executed for this documentation update.

Check catalog loading, cart changes, sign-in, and API error handling individually. Review the checkout implementation before attempting a test transaction.

## Limitations and next steps

- The checkout code uses a customer object's _id field and accepts client-supplied item data; these need validation against the intended Stripe and pricing flow.
- The payment GET handler is incomplete; the repository does not establish reliable payment verification or order fulfillment.
- No project-specific automated test script is declared.
- Authentication, authorization, payment callbacks, and inventory rules need review before deployment.

## Code review starting points

- [src/app/api/payment/route.js](<src/app/api/payment/route.js>)
- [src/app/api/catalog/route.js](<src/app/api/catalog/route.js>)
- [src/app/cart/page.js](<src/app/cart/page.js>)
