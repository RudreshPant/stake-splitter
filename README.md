# Stake Splitter

An educational, browser-based football odds and probability analysis tool built with HTML, CSS, and vanilla JavaScript.

> **Disclaimer:** This project is for educational and mathematical analysis only. It does not guarantee profits, eliminate real-world betting risks, or provide financial advice. It is not affiliated with Parimatch or any bookmaker.

## Features

- Manually enter home/draw/away, over/under 2.5 goals, and both-teams-to-score decimal odds.
- Compare implied probabilities and bookmaker margins.
- Explore theoretical allocations across mutually exclusive outcomes.
- Model scoreline probabilities using independent Poisson goal distributions fitted to input odds.
- Compare hypothetical outcomes, expected value, and approximate break-even probabilities.
- Analyze multi-leg parlays under simplifying independence and margin assumptions.
- Save inputs locally in the browser using `localStorage`.
- Responsive layout with light and dark themes.

## Tech stack

- HTML5
- CSS3
- JavaScript (no frameworks or build tools)
- Google Fonts (optional network dependency)

## Run locally

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/stake-splitter.git
   cd stake-splitter
   ```
2. Open `index.html` in your browser. No installation or backend is required.

You can also use VS Code's Live Server extension.

## How to use

1. Enter two team names and a hypothetical total stake.
2. Replace example odds with decimal odds for the markets you want to study.
3. Review the coverage table and bookmaker margin calculations.
4. Explore the stake mix and outcome probability estimates.
5. Use the parlay checker to explore how assumed margins compound across legs.

All odds are entered manually. The app does **not** fetch live odds, place bets, or connect to bookmaker accounts.

## How the math works

For a mutually exclusive, exhaustive market with decimal odds `o_i`:

- Raw implied probability: `1 / o_i`
- Sum of implied probabilities: `q = sum(1 / o_i)`
- Bookmaker overround: `q - 1`
- Theoretical equal-payout stake for outcome `i` with total `S`: `S * (1 / o_i) / q`
- Theoretical common payout: `S / q`

The scoreline model uses independent Poisson distributions for home and away goals. It fits model parameters to probabilities normalized from entered odds and adjusts its outcome-group probabilities to align with the supplied market probabilities. These are modeling assumptions, **not validated forecasts**.

The stake optimizer uses a heuristic search, not an exact proof of optimality. Parlay estimates assume independence across legs and use manually supplied margin estimates.

## Known limitations

- No live odds or official sports-data feed.
- No backend, database, authentication, or API.
- Predictions depend on bookmaker odds and simplifying model assumptions.
- Same-match parlay outcomes are correlated; the parlay checker is not suitable for them.
- Displayed coverage payouts ignore real-world settlement rules, changes in odds, limits, voids, fees, and rejected bets.
- Input validation and automated testing need improvement.
- The project began as an AI-generated prototype; its implementation and assumptions should be independently reviewed.

## Potential improvements

- Separate HTML, CSS, and JavaScript into modules.
- Add unit tests for probability, payout, and optimization functions.
- Improve numeric validation and edge-case handling.
- Add historical-data backtesting and model calibration metrics.
- Add a Java Spring Boot REST API and PostgreSQL database for saved *simulation* scenarios.
- Add CI with GitHub Actions.

## AI assistance

Initial prototype generated with Claude, then reviewed and documented for learning and further development. Update this section as you make your own contributions.

## License

No license has been selected yet. Add one if you want to grant others permission to reuse the code.
