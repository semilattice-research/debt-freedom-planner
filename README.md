# Debt Freedom Planner

> ### 🤖🧪 Built end-to-end by Claude Fable + Semilattice
> This entire product — concept, design, copy, code, and launch plan — was built autonomously in a single session by [Claude Fable](https://www.anthropic.com/news/claude-fable-5-mythos-5) (Anthropic's frontier model), with every major decision driven by simulated-audience research on [Semilattice](https://semilattice.ai). Four studies on 804 simulated UK adults chose the product (from three validated concepts), the headline (from five tested options), the trust posture, and the usability fixes — before a single human user saw it. The complete paper trail: [decision graph](https://semilattice-research.github.io/debt-freedom-planner/docs/decision-graph.html) · [product log](PRODUCT_LOG.md).

**Live tool: https://semilattice-research.github.io/debt-freedom-planner/**

A free debt payoff calculator for UK consumers. List your debts (credit cards, overdrafts, loans, car finance, BNPL, store cards), say what you can pay each month, and instantly see:

- **Your debt-free date**
- **Interest and time saved** compared with paying only the minimums
- **The payoff order** — highest-interest-first (avalanche) vs smallest-balance-first (snowball), compared
- **Exactly what to pay on each debt this month**, plus the full month-by-month plan

**No signup. No bank connection. No tracking.** Everything is calculated in your browser and your numbers never leave your device (saved only to your own browser's local storage so the page remembers them).

![Full page screenshot](docs/dfp-fullpage.jpeg)

## How it was built

Every product decision was driven by simulated-audience research on [Semilattice](https://semilattice.ai) (UK Adults 2026 – Consumer Finance audience, 804 simulated respondents, 90% benchmarked accuracy): discovery of the highest-pain money problems, a three-concept head-to-head, landing headline testing, and a usability test of simulated users on this live URL. The paper trail:

- [`PRODUCT_LOG.md`](PRODUCT_LOG.md) — plain-English log of every step, the data, and the decisions it drove
- [`DECISION_GRAPH.md`](DECISION_GRAPH.md) — the full inheritance graph: simulation → data point → decision → next simulation/spec/build ([interactive version](https://semilattice-research.github.io/debt-freedom-planner/docs/decision-graph.html))
- [`docs/superpowers/specs/`](docs/superpowers/specs/) — the design spec
- [`LAUNCH.md`](LAUNCH.md) — distribution plan

## Running locally

It's a static page with no build step:

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

Run the calculation engine tests (Node 18+):

```sh
node --test test/engine.test.js
```

## Important

This is a calculator, not advice. It does not provide financial or debt advice and is not regulated by the Financial Conduct Authority. Figures are estimates based on the numbers you enter and fixed interest rates. If you're struggling with debt, get free, regulated help: [StepChange](https://www.stepchange.org), [National Debtline](https://nationaldebtline.org), or [MoneyHelper](https://www.moneyhelper.org.uk).
