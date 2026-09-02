# Elixir Crab 🦀

Native UI and Rust tooling for Elixir.

Elixir Crab builds tools for native software that keeps application behavior,
state, supervision, and public contracts in Elixir while using Rust for bounded
platform mechanics and performance-sensitive work.

## Start here

| Project | What it does | Hex |
| --- | --- | --- |
| [gpui](https://github.com/elixir-crab/gpui) | Declarative native desktop UI for Elixir/OTP, with GPUI windows, HEEx-style views, native controls, testing, and remote displays | [![Hex](https://img.shields.io/hexpm/v/gpui.svg)](https://hex.pm/packages/gpui) |
| [rustq](https://github.com/elixir-crab/rustq) | Typed Rust and Rustler code generation from Elixir, including quasiquoting, ASTs, and generated NIF boundaries | [![Hex](https://img.shields.io/hexpm/v/rustq.svg)](https://hex.pm/packages/rustq) |

## How it fits together

```text
Elixir application
├── gpui                    — declarative applications, sessions, snapshots, and UI
│   ├── gpui_components     — conventional controls backed by gpui-component
│   └── gpui_native         — statically composed vanilla and component native hosts
└── rustq                   — generated Rust, Rustler boundaries, codecs, and native glue
```

## GPUI

[GPUI](https://github.com/elixir-crab/gpui) keeps authoritative application
state, window topology, UI composition, events, and accessibility policy in
Elixir. Rust owns the native event loop, rendering, focus, text shaping, IME,
measurement, and platform windows. The same application can use native,
deterministic test, or remote displays.

The project is distributed as three coordinated packages:

- `gpui` provides renderer-independent application, UI, text, resource, remote,
  and testing contracts.
- `gpui_components` provides conventional declarative controls rendered by
  `gpui-component`.
- `gpui_native` provides complete RustlerPrecompiled vanilla and component
  hosts while retaining source-build fallback.

## RustQ

[RustQ](https://github.com/elixir-crab/rustq) turns typed, Elixir-shaped code
into readable Rust. It can derive Rust signatures, codecs, Rustler entrypoints,
Elixir stubs, Cargo projects, and complete NIF boundaries from ordinary Elixir
modules and typespecs.

RustQ scales from zero-handwritten-Rust NIFs to schema-driven native libraries
that retain substantial handwritten Rust for domain and platform mechanics.

## Why this exists

Native Elixir software should be able to retain OTP ownership without
maintaining repetitive boundary code or moving application policy into Rust.
Elixir Crab projects make the boundary typed, inspectable, generated where
appropriate, and narrow enough that each runtime does the work it is best at.
