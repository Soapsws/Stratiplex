# Stratiplex

A parallel simulation sandbox for algorithmic game theory. The Rust engine and JavaScript viewer are scaffolded; the simulation contracts and interface connection will be implemented after L5 is defined.

## Layout

- `engine/`: Rust library and executable. The library will hold game, run, scheduling, result, and replay logic; the executable is the entry point for local use.
- `viewer/`: Vanilla JavaScript app using Vite for development and builds.
- `docs/architecture.md`: Agreed architecture and open L5 decisions.

## Local commands

From this directory:

```sh
cargo check
cargo run -p stratiplex-engine
cd viewer && npm install && npm run dev
```

The Rust executable currently prints a setup message. The viewer currently displays a placeholder. They do not yet communicate.

