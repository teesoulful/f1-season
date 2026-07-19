# F1 Season Tracker

Championship table for our multiplayer Grand Prix season. The game won't run a
season for three players, so the points get tracked by hand.

Live: https://teesoulful.github.io/f1-season/

## What it does

One grid, the whole season on screen. Rows are the rounds, columns are the three
of us. Click a cell, type the finishing position, and it does the points.

- `R` (or DNF, or X) marks a retirement. Blank means that person sat the round out.
- Enter or the arrow keys walk down a column, so a race night is a few keystrokes.
- **SPR** adds a sprint to a weekend. It opens a second line above the Grand Prix
  with its own cells, because a sprint weekend runs both races and **pays both**.
  It does not replace the Grand Prix.
- Race names are editable in place, `×` deletes a round, **Add race** appends one.
- Driver names are editable by clicking them in the standings at the top.

## Scoring

| | P1 | P2 | P3 | P4 | P5 | P6 | P7 | P8 | P9 | P10 |
|---|---|---|---|---|---|---|---|---|---|---|
| Grand Prix | 25 | 18 | 15 | 12 | 10 | 8 | 6 | 4 | 2 | 1 |
| Sprint | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | | |

A retirement scores nothing but still counts as a race started. The grid is 20
cars, so anything typed above 20 clamps to 20. Wins, podiums and races counted
are Grand Prix only, so a sprint win isn't logged as a race win; points come off
both. Ties break on points, then wins, then podiums, then best finish.

## Sharing scores

There is no shared database. Everyone who opens the link gets their own copy,
saved in their own browser. What moves the scores around is the **Copy share
link** button: it packs the whole season into the end of the URL, roughly 500
characters for a full season. Send that link and whoever opens it sees exactly
the table you had when you copied it. Same trick moves a season between a
laptop and a phone.

If someone opens a shared link when they already have results saved, the page
asks first: **Load theirs** or **Keep mine**. It never silently wipes a season.

## The calendar

Thirteen rounds, set in `CALENDAR` near the top of the script in `index.html`:

Australia, Japan, Bahrain, Saudi Arabia, Imola, Monaco, Canada, Austria,
Belgium, Monza, Singapore, Las Vegas, Abu Dhabi.

**Reset calendar** restores that list. Rows can be renamed, added or deleted in
the page at any time without touching the code; edit `CALENDAR` only if the
season list changes for good.

## Running it

It's one static file with no build step and no dependencies. Open `index.html`
in a browser, or serve the folder:

```
python3 -m http.server 8643 --directory "/Users/tee/Documents/F1"
```

Pushing to `main` redeploys GitHub Pages.
