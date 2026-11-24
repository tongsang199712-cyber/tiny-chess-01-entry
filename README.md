# tiny-chess-01 entry

A chess engine in 4,026 bytes of Python (standard library only), written for
the make.fun tiny-chess-01 competition.

`main.py` is an lzma-packed payload with its unpacker (the size rule counts
the packed bytes). The unpacked engine: 0x88 board, negamax alpha-beta with
PVS, transposition table, quiescence search, null-move pruning, late-move
reductions, check extensions, MVV-LVA/killer/history move ordering, and a
material + piece-square evaluation with bishop-pair, passed-pawn, pawn-shield
and king-proximity terms. It searches a fixed node budget (65,000 nodes per
move), never a clock, so every game is deterministic and replays exactly.

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(POST /game, /move). No model calls.

License: MIT (see LICENSE).
