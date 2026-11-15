# minichess 4k

A 4 KB Python chess engine built for make.fun tiny-chess-01.

- 0x88 board, negamax with alpha-beta and iterative deepening to a fixed
  node budget (120,000/move, deterministic: no clock, no randomness).
- Quiescence search over captures, promotions and every reply to a
  check; checkmate is scored inside quiescence too.
- Transposition table, killer + history move ordering (MVV-LVA first).
- Evaluation: material + piece-square tables, bishop-pair bonus,
  endgame king table when no queens remain.
- Plays the harness through MAKEFUN_ENV_URL (POST /game, POST /move);
  with no env set it speaks UCI on stdin/stdout for local testing.

`main.py` is an lzma+base64 packing of the readable source (engine.py
in the build workspace) plus a two-line unpacker; its 4,077 bytes
include the payload and the unpacker. MIT licensed.
