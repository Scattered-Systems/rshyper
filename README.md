# rshyper

[![crates.io](https://img.shields.io/crates/v/rshyper?style=for-the-badge&logo=rust)](https://crates.io/crates/rshyper)
[![docs.rs](https://img.shields.io/docsrs/rshyper?style=for-the-badge)](https://docs.rs/rshyper)

**A general-purpose Rust hypergraph framework, under active development.** The published version is [v0.1.9](https://github.com/pzzld-org/rshyper/releases/tag/v0.1.9). The [v0.2.0 draft PR](https://github.com/pzzld-org/rshyper/pull/100) is not yet qualified or released; it originally declares 0.1.10 in its manifest, pending compatibility/version review.

## Workspace

| Crate | Role |
| --- | --- |
| `rshyper-core` | Nodes, edges, incidence and index/type abstractions |
| `rshyper-hmap` | In-memory map-backed hypergraph |
| `rshyper-algo` | BFS, DFS, A* and Dijkstra implementations; precise higher-order semantics are under qualification |
| `rshyper` | Public facade, feature forwarding and macros |

Hypergraph data types and operators are **not** a durable storage engine, a verified distributed protocol, or a universal directed shortest-path contract.

## Installation

For the released crate:

```toml
[dependencies]
rshyper = { version = "0.1.9", features = ["hyper_map", "macros"] }
```

See the [examples directory](rshyper/examples) and [QUICKSTART.md](QUICKSTART.md). The previous README's inline macro example was stale against the published API; the next sprint must restore a compiled and CI-checked usage example before release. APIs may change in the draft patch.

## Development

```sh
cargo test --workspace --locked
cargo fmt --all -- --check
cargo clippy --workspace --all-targets --locked -- -D warnings
cargo test --workspace --doc --locked
nix flake check --no-write-lock-file
nix build --no-write-lock-file
```

**These are required validation targets, not an assertion that the current draft passes.** Until [#108](https://github.com/pzzld-org/rshyper/issues/108) is accepted, the toolchain/flake selection is floating and the full CI/feature matrix is unqualified. Check local `rust-toolchain.toml`, `flake.nix`, `flake.lock`, the Cargo feature graph and CI before attempting nightly/no_std or WASM-specific targets.

## Project coordination

- [AGENTS.md](AGENTS.md): agent worktree, source-custody and acceptance contract.
- [Draft patch handoff](.artifacts/docs/v0.2.0-handoff.md): existing branches, prioritized release gates and low-quota CC execution.
- [Puzzled Linear project](https://linear.app/pzzld/project/rshyper-6605c340fb75): objectives/milestones.
- [GitHub issues](https://github.com/pzzld-org/rshyper/issues): engineering and test evidence.
- Silo project `rshyper`: maintained formal semantic contract and research notes; external consumers such as Chaos own storage and execution.

Contributions should include reproducible failures/tests, exact environment, and compatibility notes. See [CONTRIBUTING.md](CONTRIBUTING.md) and [SECURITY.md](SECURITY.md).

Licensed under [Apache-2.0](LICENSE).
