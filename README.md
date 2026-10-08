# gray-header

Inject `~/.gray/header.txt` — a user-managed banner/preferences file — into
every turn. Port of pi's `system-prompt-header` extension.

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
