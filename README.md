# WebVault starter template

A ready-to-deploy Markdown vault with [WebVault](https://github.com/marconucara/web-vault)
already wired in. Deploy it to Cloudflare Workers in a few clicks, get a working
web reader/editor with a small starter vault, then point it at your own notes.

New to WebVault? It's a static web viewer and editor for Markdown knowledge
vaults — browse notes in a browser, edit them with a WYSIWYG editor, and publish
isolated public share links. See the [WebVault README](https://github.com/marconucara/web-vault#readme).

## 1. Deploy to Cloudflare

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/marconucara/web-vault-template/tree/main/.web)

Clicking the button **clones this template into your own GitHub account** and sets
up a Cloudflare Worker connected to it. Follow the flow; the build settings come
from `.web/wrangler.toml`.

> **Keep your new repository private** — it will hold your notes. Set it private
> in your GitHub repo settings right after the button creates it.

After the first deploy the site is **public** and read-only. The next two steps
turn on editing and privacy.

## 2. Turn on editing

Add a GitHub token so the in-browser editor can commit changes back to your repo.

- Worker → **Settings → Variables and Secrets** → add a **Secret**
  `GITHUB_TOKEN` = a fine-grained GitHub token with **Contents: write** on your
  repository only. Without it the site is read-only; the token lives only as a
  Worker secret and never enters the site bundle.

## 3. Make it private (recommended)

Gate the whole site with **Cloudflare Access / Zero Trust**, keeping only
`/shared/*` public. The exact steps — including the `*.workers.dev` Access
hostname syntax (production + preview) and the `/shared` `Bypass` — are in
WebVault's [**DEPLOY.md**](https://github.com/marconucara/web-vault/blob/v0.4.0/DEPLOY.md),
which is the full runbook for tokens, Access, and troubleshooting.

## 4. Make it yours

- Edit or delete `welcome.md` and add your own `.md` notes anywhere in this repo.
- Saved views live in `views/*.yml`.
- Every push rebuilds and redeploys automatically. Editor commits do too — as
  long as the build watch path reaches the vault (see DEPLOY.md).
- To use an **existing** vault instead of this starter, move the `.web/` folder
  into that vault's repository (or set `VAULT_DIR`) and connect that repository.

## What's in here

- `welcome.md`, `views/` — the minimal starter vault (plain Markdown). This
  repository is shaped exactly like a normal Markdown vault with a `.web/` folder
  inside it.
- `.web/` — the WebVault deployment shell: config plus the `web-vault` dependency.
  It owns no app code; the application and build pipeline live in the `web-vault`
  package. Don't hand-edit generated build artifacts (`.web/.wv/`, `.web/dist/`).

## Prefer setting up an existing vault by hand?

Two onboarding paths exist — pick the one that fits:

- **This template + one-click** (above) — start from near-zero, no coding agent.
- **Agent-driven setup into an existing vault** — if you already have a Markdown
  vault and a coding agent, see
  [WebVault's SETUP.md](https://github.com/marconucara/web-vault/blob/v0.4.0/SETUP.md).

## License

The `web-vault` package is AGPL-3.0. This starter content is yours to change.
