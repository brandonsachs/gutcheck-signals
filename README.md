# GutCheck signal record

The public, append-only record of every signal called by [gutcheck.bet](https://gutcheck.bet). This repo exists so the track record can be checked by someone who does not trust us.

## The files

**`signals/log.json`** is the live record. The site seals every ATP and WTA singles match's pre-match book at first serve, and once a night each finished match's sealed book is read and the verdict it carried is written here as the lock, timestamped at first serve. Once locked it is never rewritten. Until 2026-10-26 a scanner committed each lock within half an hour of first serve, so locks before that date can be audited against their commit timestamp; later locks are committed the night after the match.

**`signals/record.json`** is the scorecard computed from the live record: wins, losses, win rate against the implied probability at the locked price, and return at those prices, split by when the signal locked.

**`signals/reconstructed.json`** is history from before the tracker existed, rebuilt from Polymarket trade history. It uses the identical signal rule and lock logic, and wallet grades are walk forward, meaning a wallet's grade for a match comes only from matches that had already settled when that match started. These calls were not published before the matches resolved, so they carry a weaker standard of proof, and the file says so in its own provenance field. The two records are reported separately and never summed.

## What the signal is

We grade every Polymarket wallet on its resolved ATP and WTA record. The signal is alignment: wallets with winning records leaning one side of a match while wallets with losing records lean the other, each by a meaningful amount. The signal locks at first serve from the last pre-match reading. If nothing was aligned before the match, the first aligned reading within thirty minutes of the start locks instead, and is labelled separately. After the lock, later money movement is logged as a footnote but can never change the call.

Fewer than one match in ten produces a signal. The record includes every one that did, hits and misses alike.
