# GitHub (accounts)

Checks that a GitHub account is a person's: they make a gist on github.com, signed in as that account, holding their
Weave id, and give its address. Anyone's Weave asks GitHub whether the gist belongs to that account and holds that
line, so nobody has to take anyone's word for it. Delete the gist, and the account is no longer theirs in Weave.

It's a verifier: a client app every Weave runs when it needs to know (on a hub, for a project's GitHub access). It
reaches `api.github.com` only, without signing in.

## Where it lives

This repository is its only source. Weave ships it by pinning one of its releases (Weave's
`packages/shipped/pinned.json`: this repository, a tag and the archive's SHA-256), so what Weave ships is exactly
the file released here. A new version: tag it here, then move the pin in Weave.

## Building and releasing

```
npm install
npm run build              # → github-verify.wasm
```

A tag `v*` builds it on GitHub and attaches `weave-github-verify.tar.gz` (the component, `weave.app.json` and this README) to a
release (`.github/workflows/release.yml`).

`wit/service.wit` is Weave's service interface (`packages/sdk/wit` in Weave's repository), copied here to build against.
