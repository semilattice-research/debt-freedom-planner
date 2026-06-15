# Product Build Log

**Goal:** Ship a free software product for UK consumers in personal finance and get 100+ users.
**Approach:** Use Semilattice simulated UK audiences for every major product, design, and marketing decision; build a no-signup web app; ship fast.

---

## 2026-06-12 — Discovery

**What we did:** Ran a Semilattice **User Research** study ("Understand your audience") against the **UK Adults 2026 – Consumer Finance** audience (804 simulated UK adults, 90% benchmarked accuracy).

📊 **Full results:** http://app.semilattice.ai/share/simulation/4d51bac5-793d-4f12-ad37-9204facee839

**What we asked:** What frustrates UK adults most about managing money, how they currently cope, what they'd want from a free tool that doesn't connect to their bank, and what builds trust.

**Why:** We haven't picked a concept yet. Constraints we fixed up-front: free web app, no bank connection (no Open Banking licensing), useful in the first session without signup.

**Result (804 respondents):**
- **Budgeting is the #1 frustration (46.6%)** — 5x bigger than the next problem (debt payoff, 10%). The #1 trigger for trying a new tool is "realising I don't know where my money goes" (31.7%).
- **People want advice, not dashboards** — the biggest complaint about existing money apps is "they don't give useful, personalised advice — just data" (39.7%).
- **No bank connection is the right call** — 93.8% prefer or insist on tools that don't link to their bank.
- **Trust is fragile** — 85.5% would abandon a tool that shares data with third parties. Trust is built by FCA approval (39.3% — we can't claim this) and clearly explaining how the tool makes money (22.8% — we can and will).
- **First-visit feature pull**: budget calculator 29.9% > debt payoff planner 22.3% > financial health check 19.9% > bill audit 18.2%. Tax/pension/credit-score tools scored near zero.
- **100% said they'd probably or definitely return** if a free tool gave a clear answer in under 5 minutes with no signup.

**Decisions made from this data:**
1. Build a budgeting-led tool that gives specific personalised advice, not just charts.
2. No bank linking, no signup, data stays on the device.
3. Put "how this is free" transparency on the page; never claim FCA approval.

---

## 2026-06-12 — Concept head-to-head

**What we did:** Ran a Semilattice **feature prioritisation** study on the same UK Consumer Finance audience, testing 3 concepts derived from discovery: **Money Snapshot** (2-min spending breakdown vs UK households + 3 actions), **Debt Freedom Planner** (fastest/cheapest payoff plan + debt-free date), **Money MOT** (5-min health check, score /100, action plan).

📊 **Full results:** http://app.semilattice.ai/share/simulation/fad3e069-8821-433e-a4a8-5ae99ea1423e

**Result (804 respondents):**
- **Debt Freedom Planner won decisively: 45.8% would try it first** (Money MOT 32.9%, Money Snapshot 21.3%) — even though only 11.1% are actively paying off debts. Concrete outputs (debt-free date, exact payments) appeal broadly.
- **Strongest advocacy by far**: 67.6% would *definitely* recommend the Debt Planner after using it, vs 27.8% (Snapshot) and 17.6% (MOT's score mechanic).
- **Word-of-mouth is the channel**: 84.3% would send the link to a friend/family member if the tool is useful; 95.6% say a trusted recommendation is what makes them try an unknown brand.
- **Copy guidance**: people want "clarity" (63%) and "a plan" (29.4%); a "score" barely registers (6.9%).
- **Speed**: 56% want value in under 2 minutes; 31% will invest 5+ minutes if it's worth it → instant headline result, then optional depth.

**Decisions made from this data:**
1. **Build the Debt Freedom Planner** as the product.
2. Make one-tap sharing a core feature on the results screen (not an afterthought).
3. Lead copy with clarity + plan language; skip score gimmicks.
4. Two-layer UX: debt-free date + interest saved instantly, detailed month-by-month plan below.
5. Compliance: frame as a calculator/information tool, NOT regulated debt advice; signpost StepChange, National Debtline, MoneyHelper.

---

## 2026-06-12 — Landing headline test

**What we did:** Ran a Semilattice **message testing** study (same UK Consumer Finance audience, 804 respondents) comparing 5 landing headlines for the Debt Freedom Planner.

📊 **Full results:** http://app.semilattice.ai/share/simulation/916fc331-c222-4e14-8946-4e6dda7c9f85

**Result:**
- **Winner: "Stop guessing. See exactly when you'll be debt-free and how to get there faster — free."** — 46.7% in forced choice (more than double the runner-up) and the highest "definitely would click" (46.9%). It works because it names a frustration people already feel.
- **"60 seconds" claims hurt**: 62.7% find them unbelievable, and speed is the least important factor (0.1%). Removed all speed claims.
- **Privacy messaging is double-edged**: "no signup, no bank connection" strongly reassures 47% but makes 20.5% more suspicious → keep it visible but calm, paired with a "Why is this free?" explainer.
- **Distribution insight**: 52.4% decide based on trusting the source; MoneySavingExpert is the first port of call for 50.4% of debt-help seekers → launch via trusted communities, not ads.

**Decisions made from this data:**
1. Hero headline = the "Stop guessing" line, verbatim.
2. No speed promises anywhere in the product.
3. Trust strip below the hero (not in it), with honest "Why is this free?" link.
4. Launch plan prioritises trusted communities (Reddit UK personal finance spaces, MSE forum) over any paid channel.

---

## 2026-06-12 — Build

**What we did:** Wrote the payoff calculation engine test-first (11 unit tests, all passing): monthly interest at APR/12, minimum payments + surplus to target debt (avalanche = highest APR, snowball = smallest balance), rollover when a debt clears, minimums-only baseline comparison, never-clears warnings, 50-year cap. Built the single-page site (vanilla HTML/CSS/JS, no build step, localStorage only), verified it end-to-end in a real browser (fixed one bug: the "Focus" tag marked the largest payment instead of the debt receiving extra money), and shipped it.

**Live at: https://semilattice-research.github.io/debt-freedom-planner/** (GitHub Pages, repo `semilattice-research/debt-freedom-planner`).

Implements every validated decision: "Stop guessing" hero verbatim, no speed claims, calm trust strip + "Why is this free?", instant debt-free date headline with depth below, share buttons (Web Share/WhatsApp/copy) with "sharing sends only the link — never your numbers", not-advice disclaimer with StepChange/National Debtline/MoneyHelper links.

---

## 2026-06-12 — Usability test on the live site

**What we did:** Ran a Semilattice **User Journey** study — simulated UK Consumer Finance users attempting the full flow on the live URL (land → enter debts → budget → get plan), watching for stalls around APR/minimum-payment inputs, budget comprehension, strategy-toggle understanding, and trust reactions.

📊 **Full results:** http://app.semilattice.ai/share/simulation/e974d13d-3f0e-4699-b4fe-6afda10b6764

**Result (5 simulated sessions on the live site):**
- **100% task completion**, all in 97–114 seconds — everyone got their debt-free date, savings, monthly payments, and understood both strategies.
- **Top trust-builders:** the privacy messaging ("your numbers never leave this device" — praised by all 5) and the overdraft warning that the £25 minimum barely covers £26.60 monthly interest (4 of 5 called it out; "it felt like the tool was actually looking out for me").
- **All 5 said they would share or recommend the tool.**
- Three minor issues: "Cheapest first" label is non-standard terminology; the example button was slightly hard to find; finding real APRs feels like effort.

**Decisions / fixes shipped from this data:**
1. Renamed strategies to "Highest interest first (avalanche)" and "Smallest balance first (snowball)".
2. Example button made prominent ("Not sure where to start? See it with example numbers →") and moved above the form.
3. Added "or in your banking app" guidance for finding APRs.

---

## 2026-06-12 — Launch plan

**What we did:** Wrote the distribution plan (`LAUNCH.md`) directly from the data: trusted communities over ads (S3: 52.4% decide on source trust; MSE is the first stop for 50.4% of debt-help seekers; 84.3% share useful tools person-to-person). Drafted ready-to-post copy for Reddit (r/UKPersonalFinance via their rules-compliant route, r/DebtFreeUK and similar), the MoneySavingExpert Debt-Free Wannabe forum, Show HN, and Product Hunt. Success metric: 100+ unique visitors in GitHub Pages traffic stats with engagement evidence within 14 days of posting.

**Note:** posting needs real community accounts, so the drafts are ready for Joseph to paste (or to review before I post anywhere we have access).
