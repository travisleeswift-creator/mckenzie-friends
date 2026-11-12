# McKenzie Friends — Court Support

Installable PWA (app shell + sidebar) for Travis Lee Swift's McKenzie-friend and case-preparation service in England & Wales: nine AI specialist desks, booking requests, pricing, and a passcode-gated owner Office.

Live: https://mckenzie-friends.travisleeswift.workers.dev

## Files (`public/`)
- `index.html` — the whole app (no build step)
- `manifest.webmanifest` — PWA manifest
- `sw.js` — service worker (offline app shell; never caches AI or webhook calls)
- `icon-192.png`, `icon-512.png`, `icon-maskable.png`

## Deploy (Cloudflare Workers, free tier)
`node scripts/deploy-gen.mjs` writes `.deploy/worker.js` (all of `public/` embedded) and `.deploy/deploy-connector.js` (upload + enable workers.dev route via the Cloudflare API).

## Notes
- AI: set the endpoint in Office → Connectors. The default "claude" preset only works while previewing inside Claude; on this site switch to Ollama/Qwen, OpenRouter, DashScope or your own proxy. Keys typed in the browser are visible to visitors — proxy them for public use.
- Data is stored on the visitor's device (localStorage). The Office passcode is a client-side gate only.
