> **DEPRECATED.** The `-all` aggregators are retired — the default bundle is defined by `@plurnk/plurnk-service`'s own dependencies; optional plugins are installed individually. See `plurnk/plurnk-service` MIGRATION.md.

# @plurnk/plurnk-execs-all

Batteries-included bundle for [plurnk-service](https://github.com/plurnk/plurnk-service)'s `exec` scheme. **It ships no code** — it's a single dependency that pulls in the [plurnk-execs](https://github.com/plurnk/plurnk-execs) framework plus every first-party runtime executor, **flat**, so one install surfaces them all to the framework's `discover()` scan.

```
npm i @plurnk/plurnk-execs-all
```

Bundles:

| | runtimes |
|---|---|
| `@plurnk/plurnk-execs-common` | sh, bash, node, python(3), perl, ruby, php, lua, deno, bun, tcl, bc, awk |
| `@plurnk/plurnk-execs-search` | search + SearXNG categories |
| `@plurnk/plurnk-execs-sqlite` | sqlite |
| `@plurnk/plurnk-execs-wasm` | wat, wasm |
| `@plurnk/plurnk-execs-git` | git, gh |
| `@plurnk/plurnk-execs-jq` | jq |

## Why a bundle, not framework deps

The framework stays **contract-only** so it has no circular deps and so its `discover()` scan can find executors at the top level of `node_modules`. This aggregator depends on the daughters *directly* (not through the framework), so npm hoists them flat — discovery sees them. A **third party** publishes their own executor under their own scope and installs it alongside; the same scan finds it, no bundle membership required. The bundle is just the convenient default, never a gate.

Want a subset? Skip this and depend on the individual executor packages you want — discovery treats them identically.