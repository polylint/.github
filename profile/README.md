<!-- markdownlint-disable MD033 MD041 -->
<div align="center">

<img src="assets/banner.svg" alt="polylint — Rust linters built for agents" width="820">

**Fast linters and formatters, written in Rust, for codebases that agents work in.**

[Tools](#tools) · [Built for agents](#built-for-agents) · [Principles](#principles) ·
[Contributing](#contributing)

</div>

---

Coding agents write a lot of code quickly, and that code still has to pass checks. The tools here keep those checks
quick enough to run on every edit and every commit. Each one is a single native binary with no runtime to install. It
reports in a form an agent can act on, and it can fix what it finds. Every tool is useful on its own, and the polylint
CLI (`poly`) can also run the others as engines under one config.

## Tools

| Tool                                                   | What it does                                                                                                                                                                                                                           | Docs                                                                |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [**polylint**](https://github.com/polylint/polylint)   | One linter and formatter for every language in a repository: the `poly` binary, one `poly.toml`, engines such as ruff, oxc, biome and mago fetched on demand, a tree-sitter tier for 300+ more languages, git hooks and commit linting | [polylint.github.io/polylint](https://polylint.github.io/polylint/) |
| [**skif**](https://github.com/polylint/skif)           | Dependency and package-manager linter, auditor and enforcer for JavaScript and TypeScript, with first-class monorepo support; replaces sherif, syncpack and knip with one binary                                                       | [polylint.github.io/skif](https://polylint.github.io/skif/)         |
| [**adrlint**](https://github.com/polylint/adrlint)     | Linter and formatter for [MADR](https://adr.github.io/madr/) architecture decision records: structure, sequential numbering, and content hashes that keep accepted decisions immutable                                                 | [README](https://github.com/polylint/adrlint#readme)                |
| [**uncomment**](https://github.com/polylint/uncomment) | AST-accurate comment removal and tag-comment linting for 300+ languages, built on tree-sitter                                                                                                                                          | [README](https://github.com/polylint/uncomment#readme)              |

More tools will be added here as they are released.

Homebrew users can add the tap once and then install any tool from it:

```sh
brew tap polylint/tap
```

On Windows, add the Scoop bucket the same way:

```sh
scoop bucket add polylint https://github.com/polylint/scoop-bucket
```

npm packages are published under the [`@polylint`](https://www.npmjs.com/org/polylint) scope. Each repository's README
covers its other install channels: crates.io, PyPI, prebuilt archives and a GitHub Action.

## Built for agents

- **Machine-readable output.** Results come out as JSON, and as TOON or SARIF where a tool supports them. The exit
  codes are stable, so an agent or a CI job can act on a result without parsing prose.
- **MCP servers and agent plugins.** polylint and skif include MCP servers. Plugins and skills are available for
  Claude Code, Codex, Cursor, OpenCode and other agent hosts.
- **Fixes, not only findings.** Autofixes keep formatting, key order and comments. Read-only checks stay separate
  from operations that change files.
- **Fast enough for every edit.** Native Rust, run in parallel, and scoped to staged or changed files when used as
  git hooks.

## Principles

- One binary per tool, prebuilt for Linux, macOS and Windows, with signed or attested release artifacts.
- Zero-config defaults, with one TOML file when you need more.
- The CLI, git hooks, CI and MCP surfaces all share one engine, so they report the same results.
- MIT licensed.

## Contributing

Each repository has its own `CONTRIBUTING.md`. Report security issues privately, as described in
[SECURITY.md](https://github.com/polylint/.github/blob/main/SECURITY.md). Maintainers can use the
[polyrepo](https://github.com/polylint/polyrepo) to check out the whole organization as one workspace for agents.

polylint is maintained by [Na'aman Hirschfeld](https://github.com/Goldziher).
[Sponsor the work](https://github.com/sponsors/Goldziher).
