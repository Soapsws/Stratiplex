# Architecture notes

## L1 — Shape

One Run uses one fixed game and one hyperparameter set. Independent work is distributed across a bounded set of Workers. A JavaScript interface will start Runs and replay selected simulation work.

## L2 — Method

- **Run:** the entire parallel experiment.
- **Instance:** a logical group of Loops within a Run.
- **Loop:** one complete game execution; the game resets before every Loop.
- **Worker:** a reusable Rust thread that executes queued work.
- Stable Run seed, Instance ID, and Loop ID identify each Loop's random stream independently of scheduling.

## L3 — Members

- Run specification and coordinator
- Game definitions
- Loop-batch job queue and Workers
- Batch-to-Instance reducer and Run aggregator
- Replay path and JavaScript viewer

## L4 — Flow

1. The interface submits a Run specification.
2. The coordinator assigns Instance and Loop IDs and creates Loop-batch jobs.
3. Available Workers execute batches, resetting the game between Loops.
4. Batch results are reduced into one result per Instance.
5. The aggregator consumes Instance results and produces Run output.
6. Replay re-executes selected work from its saved specification and seed.

One Loop is the smallest independent unit. A batch may contain one or more Loops.

## L5 — Properties (next session)

Define boundaries, ownership, exact job and result data, seed derivation and versioning, batch sizing, failure handling, and the engine/viewer transport. These are deliberately open.
