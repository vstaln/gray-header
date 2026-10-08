<p align="center">
  <img src="assets/gray-logo.svg" alt="gray" width="96">
</p>
<h1 align="center">gray-header</h1>
<p align="center">Inject a standing banner/preferences file into every turn.</p>
<p align="center">
  <a href="https://github.com/vstaln/gray-header/blob/main/LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
  <img alt="gray plugin" src="https://img.shields.io/badge/gray-plugin-7aa2f7.svg">
  <img alt="rust" src="https://img.shields.io/badge/built%20with-rust-orange.svg">
</p>

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

---

Part of the [gray](https://github.com/vstaln/gray) plugin ecosystem —
the open-source AI agent harness. <https://gray.alignment.id>
