# smpl.fizx.uk

> Share short audio samples on Nostr — upload, play, NIP-05 tag, listen.

**Live**: <https://smpl.fizx.uk>

## Stack

- [Vite](https://vitejs.dev/) + React 18 + TypeScript
- Tailwind CSS
- [nostr-tools](https://github.com/nbd-wtf/nostr-tools)
- lucide-react

## Nostr

- **Login**: NIP-07 (browser extension) + NIP-55 (Amber callback URI)
- `kind:1063` — NIP-94 file metadata — the sample event itself
- `kind:27235` — NIP-98 HTTP auth — Authorization header for the upload endpoint

Uploads via [nostr.build NIP-96 endpoint](https://nostr.build/api/v2/nip96/upload). NIP-05 tagging in the upload form: comma-separated `name@domain` resolved at publish, attached as `['p', hex, '', 'mention']` tags. Compact / full sample list views (persisted via `localStorage`).

## Develop

```bash
npm install
npm run dev
```

## Build + deploy

```bash
npm run build
rsync -avz --delete -e "ssh -p 2121" dist/ root@88.218.206.187:/var/www/smpl.fizx.uk/
```

VPS: `88.218.206.187`. Full server / nginx / SSL / DNS notes for the wider deployment live in the local `code_vibe/CLAUDE.md` (not pushed; this README is the public-facing summary).

---

_Sister repo on the other side: <https://github.com/macos-node/smpl.upleb.uk>_
