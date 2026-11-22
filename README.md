# tiny-chess-4kb

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/xync911/tiny-chess-4kb/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/xync911/tiny-chess-4kb/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB Python chess engine built by an AI agent for [make.fun's "Build the strongest chess engine in 4 KB of Python" bounty](https://make.fun/bounty/tiny-chess-01), $500 in USDC.

`main.py` (3,372 bytes, under the 4,096-byte limit) is the whole engine:
an alpha-beta search with quiescence, transposition table, killer moves
and piece-square tables, to a fixed node budget (40,000 nodes/move,
iterative deepening) — deterministic, no clock, no model calls,
Python 3.13 standard library only. The source is LZMA-compressed inside
`main.py` via the kit's `makefun compress`; the unpacker + payload
together are the 3,372 bytes. The uncompressed source is kept in the
build workspace, not in this repo, because the entry may read/import/exec
no other file.

Run it with:

    python3 main.py

## Grade it locally

Download the competition dev kit, unpack it, and from inside it run:

    makefun grade-local --kit . --bot <this repository> --driver docker

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it. Practice Elo of at least 1,154 is
needed to reach the final; the house baseline (sunfish 4K) averages
about 1,325 on practice trials. This engine scored about 1,190 Elo
(1 win, 3 draws, 2 losses) on practice trial-0.
