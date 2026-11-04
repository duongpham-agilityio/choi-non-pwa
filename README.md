# choi-non

Monorepo (Turborepo + pnpm).

## Structure

```
apps/
  web/      Next.js PWA (@choi-non/web)
  mobile/   Expo app (TODO, not installed yet)
packages/   shared code (empty)
```

## Development

```bash
pnpm install
pnpm dev        # run all apps
pnpm build
pnpm lint
pnpm typecheck
```

Run web only: `pnpm --filter @choi-non/web dev`

## PWA (apps/web)

- Manifest: `apps/web/src/app/manifest.ts`
- Placeholder icons: `apps/web/public/icon-192.png`, `icon-512.png` — replace with real icons.
- No service worker / offline support yet. Add later (e.g. Serwist) when needed.

## Mobile (Expo) — TODO

Not initialized yet. When needed:

```bash
cd apps
pnpm dlx create-expo-app@latest mobile --template default
```

Notes for adding Expo to a pnpm monorepo:

- Add `node-linker=hoisted` to `.npmrc` at the root (Metro does not work well with pnpm's default symlinked `node_modules`).
- Name the package `@choi-non/mobile` and add `lint` / `typecheck` scripts so turbo can run them.
- Add `.expo/` to `.gitignore`.
- Put shared code (types, API client, logic) in `packages/*` and import it from both web and mobile.
- Build/deploy with EAS (`eas build`).
