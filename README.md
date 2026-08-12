# QSBS Eligibility Screener

A private, single-page preliminary screener for federal qualified small business stock (QSBS) eligibility under IRC §1202, including the July 4, 2025 statutory changes and a §1045 rollover alert.

## Features

- Historical 50%, 75%, and 100% exclusion percentages, plus post-July 4, 2025 acquisition rules
- $50 million / $75 million gross-asset tests
- Three-, four-, and five-year holding-period tiers for newly issued stock
- Per-issuer dollar limit and 10× basis calculation
- Active-business, excluded-business, redemption, and documentation flags
- §1045 six-month / 60-day rollover alert
- Advisor-question generator and print / Save PDF report
- Responsive mobile and desktop layout
- No server, cookies, analytics, local storage, accounts, or data transmission

This tool is educational and does not provide a tax opinion. QSBS is fact-intensive, state conformity varies, and professional review is essential before claiming an exclusion.

## Run locally

Download the repository and open `index.html` in a modern browser. No installation or build command is required.

## GitHub Pages

1. Open **GitHub → Repository → Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Choose **main** and **/ (root)**, then save.
4. After GitHub reports a successful deployment, the expected URL is:
   `https://rwanghx.github.io/QSBS-Screener/`

All files use relative/self-contained paths and work from the `/QSBS-Screener/` project subdirectory.

## Updating Tax Law

Tax-law constants are centralized near the beginning of the inline JavaScript in `index.html`.

1. Update `APP_CONFIG`:
   - `version`
   - `lawVerifiedThrough`
   - `lastUpdated`
2. Update `TAX_LAW` only after checking current primary authority:
   - `legacy.grossAssets` and `modern.grossAssets` for §1202 gross-asset thresholds
   - `legacy.perIssuerCap` and `modern.perIssuerCap` for exclusion dollar limits
   - `reformEffective` for the acquisition-date cutoff
   - each regime’s `tiers` array for holding-period tiers
   - `inflationAdjustments` for indexed amounts after 2026
3. Confirm the decision-engine tests at the bottom of `index.html` still pass in the browser console, add boundary tests for every changed amount/date, and manually complete the questionnaire on mobile and desktop.
4. Update the explanatory copy and this README if the statute, administrative guidance, or state-law scope changes.

The $15 million per-issuer limit and $75 million gross-asset threshold are subject to inflation adjustments for taxable years beginning after 2026. Verify published adjustments before each annual release.

## Primary legal sources

- [26 U.S.C. §1202 — Partial exclusion for gain from certain small business stock](https://uscode.house.gov/view.xhtml?edition=prelim&num=0&req=granuleid%3AUSC-prelim-title26-section1202)
- [26 U.S.C. §1045 — Rollover of gain from qualified small business stock](https://uscode.house.gov/view.xhtml?edition=prelim&num=0&req=granuleid%3AUSC-prelim-title26-section1045)
- [Public Law 119-21, §70431 (July 4, 2025)](https://www.govinfo.gov/link/plaw/119/public/21)
- [Rev. Proc. 98-48](https://www.irs.gov/pub/irs-drop/rp98-48.pdf)
- [Treas. Reg. §1.1045-1 / IRB 2007-40](https://www.irs.gov/irb/2007-40_IRB)

Federal tax law was verified through **August 12, 2026**.

## Architecture

The project intentionally consists of `index.html`, this README, and `.nojekyll`. HTML, CSS, configuration, pure decision-engine functions, UI code, and regression checks are organized in labeled sections inside `index.html` to keep future updates targeted and reviewable.
