# Token Launch Radar

Build the best token launch radar for make.fun: read a sealed snapshot of every protocol DefiLlama tracks, find the ones that still record no token and are not a wrapped or staked product of one that trades, rank them by what their launch would be worth, and show the board, a detail view for each protocol, and the steps to farm it in a web dashboard.

## Run it

```sh
MAKEFUN_OUTPUT_DIR=out node main.ts --input <snapshot.json>
```

The program reads the snapshot, scores the pre-token protocols with the model in `lib/model.ts`, writes the ranked board to `out/board.json`, writes the dashboard data beside the page, copies `dashboard/` and `screenshots/` to `out/`, and writes `out/dossier.json`.

## Model radar-2

Implied value follows from the snapshot's own figures only. The base is TVL times a tiered multiple (0.35 below $100M, 0.30 from $100M to $1B, 0.25 at $1B and above), multiplied by a growth factor from the seven-day TVL change clamped to -80 to 200 percent with weight 0.8, a maturity factor from 0.55 to 1.15 over 1,460 days with no token, and a chain factor of 1 plus 0.03 per extra chain up to 1.12. No protocol name is special-cased. The board covers the whole 40-protocol watchlist plus 160 early pre-token protocols below its floor, with 24 live-token protocols set aside with their market caps shown.

Entered in [make.fun's Build the best token launch radar](https://make.fun/bounty/token-radar-01) bounty.

## License

MIT
