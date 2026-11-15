# minichess 4k

A chess engine in 4,096 bytes of Python for make.fun tiny-chess-01.

- 0x88 board, negamax alpha-beta with iterative deepening to a fixed
  node count (80,000/move, deterministic: no clock, no randomness).
- Quiescence search over captures, promotions and every reply to a
  check; checkmate is scored inside quiescence too.
- Transposition table, killer + history move ordering (MVV-LVA first).
- Evaluation: material + piece-square tables, bishop-pair bonus,
  endgame king table when no queens remain.
- Talks to the env at MAKEFUN_ENV_URL (POST /game, POST /move);
  with no env set it speaks UCI on stdin/stdout for local testing.

`main.py` is a zlib+base64 packing of the readable source (engine.py
in the build workspace) plus a two-line unpacker; its 3,883 bytes
include the payload and the unpacker. MIT licensed.
