# WebVault starter template

A ready-to-deploy Markdown vault with [WebVault](https://github.com/marconucara/web-vault)
already wired in. Start from this repository, deploy it to Cloudflare Pages, get a
working web reader/editor with a small starter vault, then point it at your own
notes.

New to WebVault? It's a static web viewer and editor for Markdown knowledge
vaults — browse notes in a browser, edit them with a WYSIWYG editor, and publish
isolated public share links. See the [WebVault README](https://github.com/marconucara/web-vault#readme).

## 1. Get your own copy

Click **“Use this template” → “Create a new repository”** at the top of this repo
(or clone it) to get your own copy in your GitHub account.

**Keep the new repository private** — it is going to hold your notes.

## 2. Deploy to Cloudflare Pages

The site is a static build behind **Cloudflare Access** (private); only
`/shared/*` is public. The in-browser editor commits back to your repository
through a Pages Function. In the Cloudflare dashboard:

1. **Create a Pages project → Connect to Git**, and pick your new repository.
   Set the build configuration (you set this **once**; later pushes redeploy
   automatically):
   - **Root directory:** `.web`
   - **Build command:** `yarn build`
   - **Build output directory:** `dist`

2. **Add the editor token** (Settings → Environment variables → add a
   **Secret**): `GITHUB_TOKEN` = a fine-grained GitHub token with **Contents:
   write** on your repository only. Without it the deployed site is read-only.
   The token lives only as a Cloudflare secret and never enters the site bundle.

3. **Gate the site with Cloudflare Access:** an `Allow` policy over the whole
   domain, plus a path-scoped `Bypass` on `/shared/*` so share links stay public.

Deploy. Open the site (behind Access): your starter vault loads, and — with the
token set — the editor commits changes straight back to your repository.

> Why no “Deploy to Cloudflare” button? That button only supports Cloudflare
> Workers, not Pages projects, so the one-time **Connect to Git** setup above is
> the supported path here.

## 3. Make it yours

- Edit or delete `welcome.md` and add your own `.md` notes anywhere in this repo.
- Saved views live in `views/*.yml`.
- To use an **existing** vault instead of this starter, move the `.web/` folder
  into that vault's repository (or set `VAULT_DIR`) and connect that repository.

## What's in here

- `welcome.md`, `views/` — the minimal starter vault (plain Markdown). This
  repository is shaped exactly like a normal Markdown vault with a `.web/` folder
  inside it.
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
