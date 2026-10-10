<div align="center">
  <img alt="gray-header" src="assets/icon.svg" width="120" height="120" />
  <h1>gray-header</h1>
  <p><strong>Inject a user-managed banner or preferences file into every turn.</strong></p>
  <p>
    <a href="https://gray.alignment.id">Website</a> ·
    <a href="https://gray.alignment.id/plugins/gray-header">Store</a> ·
    <a href="https://github.com/vstaln/gray-header">Source</a> ·
    <a href="https://github.com/vstaln/gray">gray</a>
  </p>
  <p>
    <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-1c1c20?style=flat-square&labelColor=0a0a0b" /></a>
    <a href="https://www.rust-lang.org"><img alt="Built with Rust" src="https://img.shields.io/badge/built%20with-rust-1c1c20?style=flat-square&labelColor=0a0a0b&logo=rust&logoColor=d4a373" /></a>
    <a href="https://gray.alignment.id/plugins/gray-header"><img alt="gray plugin" src="https://img.shields.io/badge/gray-plugin-1c1c20?style=flat-square&labelColor=0a0a0b&color=7aa2f7" /></a>
  </p>
</div>

<br/>

```bash
gray plugin install gray-header
```

Inject `~/.gray/header.txt` — a user-managed banner/preferences file — into
every turn.

A sidecar plugin for [gray](https://github.com/vstaln/gray), scaffolded by
[gray-account](https://github.com/vstaln/gray-account).

## What it does

On `prompt/context` the sidecar returns the contents of
`<gray-home>/header.txt` (`$GRAY_HOME` honored, `$HOME/.gray` fallback) as
injected context — a place for standing preferences like "always be terse".
Missing or blank file → `{}` (nothing injected).

`/header show` prints the current header; `/header edit-hint` prints the
file path to edit; bare `/header` shows status.

## Wire methods

`plugin/manifest` · `prompt/context` (hook) · `command/run` (`/header`) ·
`plugin/shutdown`

## Install

```sh
gray plugin install header
```

## Develop

```sh
cargo test
gray account check      # entry point + manifest handshake
gray account publish    # check → build → release → publish to the gray registry
```

Bump `version` in `Cargo.toml` before each `publish`; the registry refuses to
republish a version.

## Tags

`gray` `plugin` `header` `rust`

---

Part of the [gray](https://github.com/vstaln/gray) plugin ecosystem —
the open-source AI agent harness. <https://gray.alignment.id>
