# equity-research-archive

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Site](https://img.shields.io/badge/site-live-1a3d6f)](https://geniustrader-harry.github.io/equity-research-archive/)

A personal archive of finished single-name investment pitches. Each entry has the full memo as a PDF and the underlying Excel DCF model with sensitivity. Produced through the [equity-research-skill](https://github.com/GeniusTrader-Harry/equity-research-skill) thesis-first workflow.

Live at **https://geniustrader-harry.github.io/equity-research-archive/**.

## Structure

```
.
├── index.html              # Landing — list of coverage
├── style.css               # One shared stylesheet
├── tickers/
│   └── SPOT/
│       ├── index.html      # Per-ticker page (embedded PDF + downloads)
│       ├── SPOT_pitch.pdf  # The memo
│       └── SPOT_model.xlsx # The model
├── assets/
│   └── favicon.svg
├── .nojekyll               # Serve as plain static; skip Jekyll
└── LICENSE
```

Plain static HTML + one CSS file. No build step.

## Add a new ticker (3-step recipe)

```bash
# 1. Copy deliverables from the working project folder
TICKER=XYZ
mkdir -p tickers/$TICKER
cp ~/Claude\ Projects/Equity\ Research/$TICKER/deliverables/${TICKER}_pitch.pdf  tickers/$TICKER/
cp ~/Claude\ Projects/Equity\ Research/$TICKER/deliverables/${TICKER}_model.xlsx tickers/$TICKER/

# 2. Duplicate the SPOT page and edit the header block
cp tickers/SPOT/index.html tickers/$TICKER/index.html
#    → edit ticker, company, date, rating, PT, current price, upside, market cap, thesis line
#    → fix relative paths if folder depth changed

# 3. Add a card on the landing page
#    → open index.html, copy the SPOT <a class="coverage-card"> block, paste at top of grid, edit

git add tickers/$TICKER index.html
git commit -m "Add $TICKER"
git push
```

Realistic time per new pitch: 5–10 minutes.

## Local preview

```bash
python3 -m http.server 8000
open http://localhost:8000
```

Or just `open index.html` — most things work via `file://`, but the iframe-embedded PDF wants an HTTP server.

## Coverage

| Ticker | Company | Date | Rating | PT |
|---|---|---|---|---|
| [SPOT](tickers/SPOT/) | Spotify Technology S.A. | 2026-05-17 | LONG | $510 (+21%) |

## Disclaimer

Personal research for educational purposes. Not investment advice. Past notes may be stale. Do your own work.
