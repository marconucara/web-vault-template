# WebVault starter template

A ready-to-deploy Markdown vault with [WebVault](https://github.com/marconucara/web-vault)
already wired in. Deploy it to Cloudflare Pages in roughly one click, get a working
web reader/editor with a small starter vault, then point it at your own notes.

New to WebVault? It's a static web viewer and editor for Markdown knowledge
vaults — browse notes in a browser, edit them with a WYSIWYG editor, and publish
isolated public share links. See the [WebVault README](https://github.com/marconucara/web-vault#readme).

## Deploy in ~one click

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/marconucara/web-vault-template)

Clicking the button clones **this** repository into your own GitHub account and
creates a Cloudflare Pages project connected to it. Then finish a few steps that
can't be automated:

1. **Make your new repository private.** It is going to hold your notes — keep it
   private. (Your public `/shared/*` links stay reachable via Cloudflare Access;
   they do not require a public repo.)

2. **Set the Pages build settings** (Cloudflare dashboard → your Pages project →
   Settings → Build):
   - **Root directory:** `.web`
   - **Build command:** `yarn build`
   - **Output directory:** `dist`

3. **Add the editor token** (Settings → Environment variables → add a
   **Secret**): `GITHUB_TOKEN` = a fine-grained GitHub token with **Contents:
   write** on this repository only. Without it, the deployed site is read-only.
   The token lives only as a Cloudflare secret and never enters the site bundle.

4. **Gate the site with Cloudflare Access:** an `Allow` policy over the whole
   domain, plus a path-scoped `Bypass` on `/shared/*` so share links stay public.

Redeploy (or push a commit) and open the site: your starter vault loads, and — with
the token set — the editor can commit changes straight back to this repository.

## Make it yours

- Edit or delete `welcome.md` and add your own `.md` notes anywhere in this repo.
- Saved views live in `views/*.yml`.
- To use an **existing** vault instead of this starter, move the `.web/` folder
  into that vault's repository (or set `VAULT_DIR`) and deploy that repository.

## What's in here

- `welcome.md`, `views/` — the minimal starter vault (plain Markdown).
- `.web/` — the WebVault deployment shell: config plus the `web-vault` dependency.
  It owns no app code; the application and build pipeline live in the `web-vault`
  package. Don't hand-edit generated build artifacts (`.web/.wv/`,
  `.web/functions/`, `.web/dist/`).

## Prefer setting up an existing vault by hand?

If you already have a Markdown vault and a coding agent, the agent-driven setup
path may fit better than this template. See
[WebVault's SETUP.md](https://github.com/marconucara/web-vault/blob/v0.3.0/SETUP.md).

## License

The `web-vault` package is AGPL-3.0. This starter content is yours to change.
