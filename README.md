# WebVault starter template

A ready-to-deploy Markdown vault with [WebVault](https://github.com/marconucara/web-vault)
already wired in. Deploy it to Cloudflare Workers in a few clicks, get a working
web reader/editor with a small starter vault, then point it at your own notes.

New to WebVault? It's a static web viewer and editor for Markdown knowledge
vaults — browse notes in a browser, edit them with a WYSIWYG editor, and publish
isolated public share links. See the [WebVault README](https://github.com/marconucara/web-vault#readme).

## Deploy to Cloudflare

> ### ⚠️ Read this before clicking
>
> The deploy button clones this template into **your** GitHub account and sets up
> a Cloudflare Worker. The flow asks for a few things — set them like this:
>
> | Field | What to do |
> |-------|------------|
> | **Project name** | Your vault's name. It becomes the default URL (`<name>.<account>.workers.dev`). |
> | **Create private Git repository** | Off by default — **turn it on** (recommended): a vault should hold your private things. |
> | **Advanced settings → Build → Path** | **`/.web/`** |
> | **Variables / secrets** (in the flow) | **Skip them here** — the welcome note walks you through them afterwards, so you don't have to guess build-vs-runtime. |

Click the button, then **come back here once the first build has finished** to continue:

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/marconucara/web-vault-template)

After the first build your site is live — **public and read-only** — with the
starter vault.

## After deploying

Carry on in the **welcome note**: it walks you through making the site private,
turning on web editing, and the rest of what WebVault does.

Open your new site and read it there — or read [`welcome.md`](welcome.md) here on
GitHub.

## Prefer setting up an existing vault by hand?

Two onboarding paths exist — pick the one that fits:

- **This template + one-click** (above) — start from near-zero, no coding agent.
- **Agent-driven setup into an existing vault** — if you already have a Markdown
  vault and a coding agent, see
  [WebVault's SETUP.md](https://github.com/marconucara/web-vault/blob/main/SETUP.md).
  You can also do it by hand: move the `.web/` folder into that vault's
  repository (or set `VAULT_DIR`) and connect that repository instead of this one.

## License

The `web-vault` package is AGPL-3.0. This starter content is yours to change.
