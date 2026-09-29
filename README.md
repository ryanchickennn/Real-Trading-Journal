# Trade Journal

A single-page trading journal for futures (and stocks). Log trades, see a monthly P&L calendar, and track win rate, profit factor, R multiples, expectancy, drawdown, and what breaking your plan costs you.

Each trade also has a top-down timeframe section (1d, 4h, 1h, 15m, 5m, 1m: bias, notes, chart link, entry timeframe) and a psychology section (state before the trade, emotions during it, an execution score, and a reflection). The overview breaks results down by all of these.

It also has:

- **Accounts:** track several prop firm or personal accounts. Each account has a starting balance, profit target, max drawdown (trailing, trailing that stops at the starting balance, or static) and a daily loss limit. The overview shows balance, target progress, drawdown left and today's P&L for each one, and the menu at the top filters everything to a single account. A trade you copied across accounts can be logged to all of them at once.
- **Daily journal:** a pre-market check-in (sleep, mood, focus, max loss, max trades, game plan) and an end-of-session review that pulls in the day's trades and flags when you broke your own limits.

No build step, no dependencies. It's one `index.html` file.

## Run it locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Put it online with GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, set Source to **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. Your journal will be live at `https://<your-username>.github.io/<repo-name>/` after a minute or two.

## Where your data lives

- **Opened from Claude:** trades save to your Claude account, private to you.
- **Anywhere else (local file, GitHub Pages):** trades save in your browser's local storage. They stay on that one browser and device, and clearing site data deletes them. Use **Settings > Export CSV** regularly as a backup.

Your trade data is never written into the repo, so a public repo does not expose your trades.

## Customizing

- Instruments and dollar-per-point values: the `INSTRUMENTS` list near the top of the script.
- Default setups and mistakes: `DEFAULT_SETTINGS`. You can also edit these in the app under Settings.
- Session times (ET): the `sessionFor()` function.
- Timeframes: the `TIMEFRAMES` list.
- Pre-trade states and emotions: `DEFAULT_SETTINGS`, or edit them in the app under Settings.
- Accounts: add and edit them in the app under Settings. Drawdown is calculated from logged trades, so treat your firm's dashboard as the source of truth.
