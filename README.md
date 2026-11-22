# tiny-chess-01

A 4KB chess engine for make.fun Tiny Chess 4KB (tiny-chess-01).

`main.py` (3,860 bytes, under the 4,096-byte limit) is the whole engine:
an alpha-beta search with quiescence, transposition table, killer moves
and piece-square tables, to a fixed node budget (40,000 nodes/move,
iterative deepening to depth 7) — deterministic, no clock, no model calls,
Python 3.13 standard library only. The source is LZMA-compressed and
base85-encoded inside `main.py`; the unpacker + payload together are the
3,860 bytes. The uncompressed source is kept in the build workspace, not
in this repo, because the entry may read/import/exec no other file.

## Grade it locally

Download the competition dev kit, unpack it, and from inside it run:

    makefun grade-local --kit . --bot <this repository> --driver docker

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it. Practice Elo of at least 1,154 is
needed to reach the final; the house baseline (sunfish 4K) averages
about 1,325 on practice trials.
