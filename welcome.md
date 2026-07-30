---
type: Note
---
# Welcome to your WebVault

This is a **starter vault** — a tiny Markdown knowledge base with WebVault already
wired in. You deployed it in roughly one click; now make it yours.

## What you're looking at

WebVault reads the Markdown notes in this repository at build time and serves them
as a fast, static site. You can:

- **Browse** notes from the sidebar and the note list.
- **Edit** a note inline with the WYSIWYG editor — changes commit straight back to
  this repository (once you set the editor token, see below).
- **Share** individual notes as isolated public `/shared/<id>/` links, while the
  rest of your vault stays private behind Cloudflare Access.

Notes link to each other with `[[wikilinks]]`, and saved views live in
`views/*.yml` — see the **Start here** view in the sidebar.

## Make it yours

1. **Keep this repository private** — it *is* your vault.
2. **Turn on editing**: add a `GITHUB_TOKEN` secret to your Cloudflare Pages
   project (a fine-grained token with *Contents: write* on this repo only). Until
   you do, the site is read-only.
3. **Add your own notes**: drop `.md` files anywhere in this repository and
   rebuild. Delete this welcome note whenever you like.
4. **Point it at an existing vault** instead: move the `.web/` folder into your own
   Markdown vault (or set `VAULT_DIR`) and deploy that repository.

Full setup and deploy notes are in this repository's `README.md`.
