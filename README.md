# Naish Luxe Touch revamp

Private review of a botanical storefront, based only on https://naish-luxe-touch.lovable.app/ and the supplied creative brief. Four source-listed products. See docs/01-audit-and-inventory.md before treating content as launch-ready.

## Run locally

Requires Node >=22.13 and pnpm. Run `pnpm install --frozen-lockfile`, then `pnpm dev`. In the managed Sites environment, use `sites-preview start "$PWD"` instead of starting the server manually. Production build: `pnpm build`. Type check: `node node_modules/typescript/bin/tsc --noEmit`.

The starter uses Vinext, React and Cloudflare-compatible Worker output. Keep its scripts, pnpm-lock.yaml and .openai/hosting.json intact. Deploy through Sites from the registered project. Do not expose credentials in source. This build has no required store API secrets because it does not process orders.

## Maintain

- `lib/catalogue.ts`: exact product names/descriptions/prices and explicit nulls for unavailable data. Currency is a literal `$`, not assumed USD.
- `components/`: reusable shopping provider, cards, product detail, hero, ingredient accordion and collection controls.
- `app/`: homepage and routes.
- `app/globals.css`: design tokens, responsive layouts, motion and reduced-motion rules.
- `public/assets/`: source masters and generated responsive WebP delivery sizes. Do not describe these as 4K. Product packaging inconsistencies remain unresolved source defects.
- `/review`: owner-facing completion and dependency handoff.

Bag is saved in `localStorage` under `naish-bag-v1`, schema validated, quantities 1–99. It is device-local and unauthenticated. Never use its subtotal to charge a customer. A production checkout must validate price, currency, inventory, variants and quantity on a server and create a provider-managed checkout session. The current checkout page clearly states ordering is unavailable. No fake order confirmations, newsletter subscriptions or account creation.

Search has an optional feature-detected WebMCP tool, `search_naish_catalogue`, which opens the same search results as the visible interface. Unsupported browsers continue normally.

## Launch integration

Obtain approved product media and missing catalogue fields, real policy text, confirmed contact information and provider credentials. Connect a store API, authoritative pricing/stock and hosted checkout. Add newsletter only after a provider and consent text are confirmed. Replace account availability dialog only after authentication exists. Verify success and cancellation paths without real purchases. Remove noindex only after content approval and production readiness.

## URL map

Original homepage anchors #home, #products, #about, #ingredients, #why-natural, #contact are retained. New routes: /collection, /products/glow-face-cream, /products/herbal-cleanser, /products/rose-hydration-serum, /products/natural-body-butter, /story, /ingredients, /contact, /support/shipping, /support/returns, /support/faq, /support/privacy, /support/terms, /checkout. No prior detail routes existed. Unknown routes display a functional 404.


## Reference replication — revision 2

The homepage follows the confirmed photographic landing reference. See `docs/06-revision-2-handoff.md` and the `/review` page. New full-resolution masters and exact prompts are retained in `design-assets/`; production uses responsive WebP assets. Generated packaging is proposed and requires brand approval. Original source photographs remain in the product galleries.
