# fcp-core-rust

## Project Overview
Shared FCP (File Context Protocol) framework for building FCP servers in Rust.
Provides tokenizer, op parser, verb registry, event log, session, and formatter.

## Architecture
Flat library crate — each module is independent:
- `tokenizer` — Quote-aware tokenizer (split on whitespace, handle quotes/escapes)
- `parsed_op` — ParsedOp struct, token classification (verb, positionals, params, selectors)
- `verb_registry` — Verb name → spec registry with reference card generation
- `event_log` — Cursor-based event log with undo/redo and named checkpoints
- `session` — Session lifecycle (new/open/save/checkpoint/undo/redo) with hooks trait
- `formatter` — Response prefix formatting and Levenshtein-based suggestions

## Commands
- `cargo test` — Run all tests
- `cargo build` — Build
- `cargo clippy -- -D warnings` — Lint check

## Conventions
- Pure Rust, no external dependencies (std only)
- Tests colocated with source (`#[cfg(test)]` modules)
