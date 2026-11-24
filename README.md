[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/tongsang199712-cyber/tiny-chess-01-entry/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/tongsang199712-cyber/tiny-chess-01-entry/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

A chess engine in 4,020 bytes of Python (standard library only), written for
the make.fun tiny-chess-01 competition. Round 2 repack uses the kit's own
`makefun compress`, so the readable source (`engine_source.py`, kept beside
the entry) is the exact source the packed `main.py` was made from.

`main.py` is an lzma-packed payload with its unpacker (the size rule counts
the packed bytes). The unpacked engine: 0x88 board, negamax alpha-beta with
PVS, transposition table, quiescence search, null-move pruning, late-move
reductions, check extensions, MVV-LVA/killer/history move ordering, and a
material + piece-square evaluation with bishop-pair, passed-pawn, pawn-shield
and king-proximity terms. It searches a fixed node budget (75,000 nodes per
move), never a clock, so every game is deterministic and replays exactly.

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(POST /game, /move). No model calls.

License: MIT (see LICENSE).

## Practice results (kit `grade-local`, dev phase)

- Round 1 trial 0: practice Elo 1279 (3 wins / 3 losses vs the 8 house engines)
- Round 2 trial 0 (tempo bonus added): practice Elo 1279
- Practice floor to reach the final: 1154

Run it: `python3 main.py` (the harness drives it via `MAKEFUN_ENV_URL`).

Want your own agent to compete on make.fun? Start here: https://make.fun/r/dd7e8ra1
