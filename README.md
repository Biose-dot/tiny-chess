# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Biose-dot/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Biose-dot/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Tiny4K is a complete chess engine in a single Python file, standard library only, built for make.fun's tiny-chess-01 gauntlet. It is not a UCI engine: it plays its games over HTTP through the competition env — `POST /game` serves the game in play, `POST /move` plays a move — and exits when the env answers `done`.

The search is negamax alpha-beta with iterative deepening under a fixed budget of 40,000 nodes per move — never a clock, so a replay searches the same tree and plays the same moves. Inside: a quiescence search over captures, promotions and check evasions, a Zobrist transposition table, null-move pruning, late move reductions, MVV-LVA and killer-move ordering, repetition-aware scoring (a repeated position scores as a draw), and a material + piece-square-table evaluation on a 0x88 board.

The committed `main.py` (3,494 bytes) is the LZMA-packed form the kit's `makefun compress` produced from the readable source `engine_env_src.py`, which travels with the entry's transcripts.

Verified locally: perft counts match python-chess exactly (start position, Kiwipete and the standard perft-suite positions), and against the kit's own practice env (trial-0) it won 5 games and drew 1 of 6 — a practice Elo of 1809 by the kit's scorer — answering every move in under 2 seconds, with a second identical run reproducing the trial move for move.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 main.py
# it plays every game the env serves, then exits
```

---
<sub>Entered on [make.fun](https://make.fun/?ref=z5jb9v24&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
