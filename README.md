# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Biose-dot/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Biose-dot/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Tiny4K is a complete chess engine in a single Python file, standard library only. It speaks UCI and searches with negamax alpha-beta and iterative deepening, a quiescence search over captures and checks, a Zobrist transposition table, null-move pruning, late move reductions, MVV-LVA and killer-move ordering, and a material + piece-square-table evaluation on a 0x88 board. The committed `main.py` (3,212 bytes) is the LZMA-packed form the kit's `makefun compress` produced from the readable source `engine_src.py`, which travels with the entry's transcripts. Verified locally: perft counts match python-chess exactly, mate-in-1 puzzles are found, and it won 30/30 games against a greedy 1-ply baseline.

## Run it

```sh
python3 main.py
# then speak UCI: uci / isready / position startpos / go depth 10
```

---
<sub>Entered on [make.fun](https://make.fun/?ref=z5jb9v24&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
