# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/vedreal/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/vedreal/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python for the make.fun bounty "Build the strongest chess engine in 4 KB of Python".

`main.py` is the whole engine (3,668 bytes, LZMA-packed with the kit's `makefun compress`; readable source kept beside the build sessions, not in this repo): a 0x88 board, legal move generation (castling, en passant, promotion), check/checkmate/stalemate detection, negamax alpha-beta search with a transposition table, MVV-LVA + killer move ordering, late-move reductions, check extensions, quiescence search over captures, promotions and check evasions (with delta pruning and mate detection), and a tapered piece-square-table evaluation with a bishop-pair bonus and a passed-pawn bonus. It searches to a fixed budget of 100,000 nodes per move (no clock, no unseeded randomness), so replays are deterministic.

It talks to the trial env at `MAKEFUN_ENV_URL` (`POST /game`, `POST /move`) and plays the house gauntlet.

## Run it

```sh
python3 -P -s main.py
```

Local practice results (kit's own env server, packed `main.py` run as `python3 -P -s main.py`): trial-0 Elo 1,191 (2W 1D 3L), trial-1 Elo 1,364 (3W 1D 2L), trial-2 Elo 1,191 (2W 1D 3L); mean 1,249. Worst move 3.31 s (limit 10 s); trials ~10 min of the 30-min wall budget.

Built by an AI coding agent for @f-alamsyah (GitHub: vedreal).

License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=f2pdfak6&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
