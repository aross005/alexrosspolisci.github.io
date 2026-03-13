# IV PASI Project Context Document

**Last updated:** 2026-03-11
**Project lead:** Alexander Ross
**Status:** Analysis complete; heterogeneity tests expanded; generalized trust DVs tested but failed placebo

---

## Project Overview

**Research Question:** Does proximity to government benefit disbursement dates affect recipients' attitudes toward government?

**Core Design:**
1. Identify survey respondents who receive government benefits with fixed monthly payment dates
2. Calculate proximity to payday (higher = closer to most recent payment)
3. Test whether proximity predicts warmer attitudes toward QC/CA government
4. Compare immigrants vs. non-immigrants

**Key Insight:** This is a natural experiment—survey completion date relative to benefit timing is essentially random, providing quasi-exogenous variation in financial state.

**Hypotheses:**
- H1 (Credit attribution): Recipients connect financial security → benefits → government, producing greater trust/attachment
- H2 (General affect): Financial security just improves mood generally (testable via attitudes toward origin country, which shouldn't be affected by QC/CA benefits)

---

## Data

| Dimension | Value |
|-----------|-------|
| File | `df_full_panel_both_samples.rds` |
| Observations | 12,117 |
| Waves | 3 (2023, 2024, 2025) |
| Panel structure | Individual ID with fixed effects |

### Benefit Disbursement Schedule

See `benefit_disbursement_schedule.csv` for full details with source URLs.

**Fixed Monthly Payment Days (Used in Analysis):**
| Payment Day | Programs | Variable | Source |
|-------------|----------|----------|--------|
| 1st | Social Assistance/Solidarity (QC), Basic Income (QC), CF Income Support | `ben_1` | quebec.ca |
| 20th | Canada Child Benefit | `ben_20` | CRA |
| 28th | Housing Benefit, CPP/QPP/OAS, Disability Pensions | `ben_28` | Retraite Québec |

**Excluded (Variable/Individual Timing):**
| Program | Issue |
|---------|-------|
| Employment Insurance | Biweekly, individual start dates |
| QPIP Parental Leave | Biweekly, individual start dates |
| Student Financial Assistance | Per-term disbursement |
| Dental Benefit | One-time application |
| Subsidized Housing | Varies by authority |

**Key Sources:**
- [Canada.ca Benefits Payment Calendar](https://www.canada.ca/en/services/benefits/calendar.html)
- [CRA Child Benefit Payment Dates](https://www.canada.ca/en/revenue-agency/services/child-family-benefits/canada-child-benefit/payment-dates.html)
- [Retraite Québec Payment Dates](https://www.retraitequebec.gouv.qc.ca/en/dates-de-paiement/Pages/dates-de-paiement.aspx)
- [Quebec Social Assistance](https://www.quebec.ca/en/family-and-support-for-individuals/social-assistance-social-solidarity)
- [Quebec Basic Income Program](https://www.quebec.ca/en/family-and-support-for-individuals/social-assistance-social-solidarity/basic-income-program)

### Analysis Samples
- **Immigrant beneficiaries**: Primary sample (~1,700 person-waves, ~560 individuals)
- **Non-immigrant beneficiaries**: Comparison sample (~2,800 person-waves)
- **Full-time workers with no benefits (immigrants)**: Paycheck placebo sample

---

## Current Methodology

### Proximity Variable

Proximity = 30 − days_since_payment (scale 1-30, where 30 = payday)

For beneficiaries receiving multiple programs, proximity = max across their payment dates (closest payday).

### Model Specification

Panel fixed effects: `outcome ~ proximity | ID`

$$Y_{it} = \beta \cdot \text{Proximity}_{it} + \alpha_i + \varepsilon_{it}$$

Positive β = closer to payday → better attitudes

**FE Specification Decision:** Individual FE only (not two-way with wave FE). Adding wave FE attenuates most effects—likely because it removes legitimate variation, since the identifying variation comes from within-person differences in survey timing across waves. Rationale explained in footnote; two-way FE results not included in appendix.

### Placebo Tests

**1. Wrong-Date Placebo:**
For each beneficiary, calculate proximity to the payment date they do NOT receive that is most distant from their actual payment date(s). Uses circular distance logic:
- 1↔20: 11 days apart
- 1↔28: 3 days apart
- 20↔28: 8 days apart

If effects are real, wrong-date placebo should be null (no reason proximity to an irrelevant date should matter).

**2. Paycheck Placebo:**
Full-time workers with NO government benefits, testing proximity to 31st (common private-sector payday). If effects were just generic "time of month," this should also show significance.

**3. Origin Country Null:**
Proximity should NOT affect attitudes toward origin country (attachment, values). This tests credit attribution vs general affect.

**4. Non-Immigrant Comparison:**
Non-immigrant beneficiaries should show weaker effects (more crystallized attitudes).

**5. Balance Checks:**
Two tests validating as-if random survey timing:
- Day of month does not predict beneficiary status
- Income does not predict survey timing (ruling out survey payment incentive confounds)

---

## Key Results

### Immigrant Beneficiaries (Treatment Effects)

| Outcome | Effect | Placebo Pass? |
|---------|--------|---------------|
| Attachment to QC | Significant (+) | Wrong-date null ✓ |
| Financial Satisfaction | Significant (+) | Wrong-date null ✓ |
| QC Values Important | Significant (+) | Wrong-date null ✓ |
| QC Friends Important | Significant (+) | Wrong-date null ✓ |
| Trust QC | Significant (+) | Wrong-date also sig ✗ |

### Placebo Results
- **Wrong-date placebo**: Generally null (validates identification)
- **Paycheck placebo (31st)**: Null effects (not generic time-of-month)
- **Origin country**: Null (supports credit attribution)
- **Non-immigrants**: Weaker/null treatment effects

### Exclusive CCB Analysis (Appendix)
- **Sample**: 408 immigrant CCB recipients who don't receive other fixed-date benefits
- **Treatment (prox_20)**: Trust QC***, Attach QC*, Financial***, QC Values**, QC Friends* significant
- **Wrong-date placebo (prox_1)**: All 9 DVs null — cleanest validation
- **Parent placebo**: 646 immigrant parents without CCB, 2/9 significant (Trust QC, Attach CAN)

### Heterogeneity Analysis
Tests whether payment proximity effects vary by individual characteristics.

**Moderator Variables:**
- `years_in_qc`: Calculated from `yearqc` (year arrived in QC). Better coverage than `yearcan` (638 vs 190 immigrant beneficiaries).
- `income_filled`: Household income (`hhincome`) on 8-point scale. Better coverage than personal income (75% vs 18%).
- `french_comp_filled`: French competency (0-10 scale from `french_competency`).
- `education_num_filled`: Education level (1-7 scale from `education_num`).
- `polknow_score`: Political knowledge (0-4 scale, sum of correct answers).
- `policyknow_score`: Policy knowledge (0-6 scale, sum of correct answers).

**Interaction Models:** `outcome ~ proximity * moderator | ID`

**Key Findings:**
- **Years in QC**: All interactions null
- **Income**: Trust QC marginally significant (p=0.09)
- **French competency**: All interactions null
- **Education**: Trust QC shows positive interaction (p=0.015) — higher education = stronger effect
- **Political knowledge**: All interactions null
- **Policy knowledge**: 3 significant negative interactions (Trust QC, Financial, QC Values) — lower knowledge = stronger effects

**Figures:**
- `@fig-interaction-years`: Marginal effect of proximity by years in QC (pooled beneficiaries)
- `@fig-interaction-income`: Marginal effect of proximity by HH income (pooled beneficiaries)
- `@fig-interaction-french`: Marginal effect by French competency
- `@fig-interaction-educ`: Marginal effect by education level
- `@fig-interaction-polknow`: Marginal effect by political knowledge
- `@fig-interaction-policyknow`: Marginal effect by policy knowledge
- `@fig-interaction-years-ccb`, `@fig-interaction-income-ccb`, `@fig-interaction-french-ccb`: Same for exclusive CCB recipients

**Appendix Tables:**
- `@tbl-app-interaction-years`: Full interaction coefficients (years)
- `@tbl-app-interaction-income`: Full interaction coefficients (income)
- `@tbl-app-interaction-french`: Full interaction coefficients (French)
- `@tbl-app-interaction-educ`: Full interaction coefficients (education)
- `@tbl-app-interaction-polknow`: Full interaction coefficients (political knowledge)
- `@tbl-app-interaction-policyknow`: Full interaction coefficients (policy knowledge)

---

## Approaches Tried (Historical Context)

### 1. Program-Specific Analysis (Failed)
Attempted separate regressions for each benefit program (Child Benefit, Housing Benefit, etc.).

**Why it failed:**
- Small n per program when spread across 31 days
- Many days had n < 10 for treatment group
- Extreme day-to-day volatility in outcome means
- Parallel trends not satisfied

### 2. Difference-in-Differences (Failed)
Treated = beneficiaries, Post = after payment day, with individual FE.

**Why it failed:**
- Non-beneficiaries showed effects as strong as beneficiaries (placebo failed)
- No clear "control group" without payment timing
- Results went opposite direction (negative post-payment effects)

### 3. Non-Beneficiary Placebo (Conceptually Problematic)
Attempted to use non-beneficiaries as placebo with proximity to arbitrary dates.

**Why it failed:**
- With multiple payment dates (1st, 20th, 28th), no single "treatment date" for non-beneficiaries
- Random assignment = arbitrary, not meaningful test

### 4. Pooled Beneficiary with Wrong-Date Placebo (Current Approach - Works)
Key insight: Use beneficiaries' own "wrong dates" as within-person placebo.

**Why it works:**
- Same individuals, same timing variation, different (irrelevant) reference date
- Null placebo validates that actual payment date specifically matters
- Large pooled sample has adequate power
- Panel FE controls for individual-level confounds

### 5. Generalized Trust DVs (Failed Placebo)
Tested whether payment proximity affects broader social/institutional trust beyond government-specific attitudes.

**Variables tested:**
- `qctrustpeople`: Trust in QC people generally (77% coverage)
- `trust_police`: Trust in police (84% coverage)
- `trust_politicians`: Trust in politicians (84% coverage)
- Origin country versions (~42% coverage — too sparse for panel FE)

**Why it failed:**
- Treatment effects appeared significant, but wrong-date placebo also showed significant effects
- Cannot distinguish real payment effects from spurious time-of-month patterns
- Removed from analysis

---

## Files

| File | Description |
|------|-------------|
| `df_full_panel_both_samples.rds` | Main data file (12,117 obs) |
| `sample_100_rows.csv` | **100 random rows from main data** — use this to quickly check column coding (cheaper than loading full RDS) |
| `pooled_beneficiary_analysis.qmd` | **Current analysis** — full paper draft with Data & Methods, Results, Discussion |
| `pooled_beneficiary_analysis.pdf` | Rendered output |
| `document_pdf.pdf` | **Prior paper** — different paper using same data (2-wave version). Use as reference for Quebec context and data background |
| `codebook.csv` | Variable dictionary |
| `benefit_disbursement_schedule.csv` | Payment dates by program |
| `PROJECT_CONTEXT.md` | This file |

### Archived (superseded)
- `analysis.qmd` — Early exploration
- `housing_benefit_analysis.qmd` — Program-specific attempt
- `parallel_trends_*.pdf` — DiD diagnostics

---

## Outcome Variables

All 0-10 scales, higher = more of construct.

| Variable | Source | Notes |
|----------|--------|-------|
| `trust_qc` | `trust_qcgov` | Trust in QC government |
| `trust_can` | `trust_cangov` | Trust in Canada (waves 2-3 only) |
| `attachment_qc` | `attach_qc` | Attachment to Quebec |
| `attachment_can` | `attach_can` | Attachment to Canada |
| `attachment_city` | `attach_city` | Attachment to city |
| `financial_satisf` | `current_financialsatisf` | Financial satisfaction |
| `life_satisf` | `current_lifesatisf` | Life satisfaction |
| `imp_qcvalues` | `imp_qcvalues` | Importance of QC values |
| `imp_qcfriends` | `imp_quebecerfriends` | Importance of QC friends |
| `origin_attachment` | `attach_origincountry` | Attachment to origin (H2 test) |
| `imp_valuesorigin` | `imp_valuesorigin` | Origin values (H2 test) |

---

## Technical Notes

### Proximity Calculation
```r
days_since_to_proximity <- function(days_since) { 30 - days_since }

# For multiple benefits, use closest payday
prox_actual = pmax(prox_1, prox_20, prox_28)  # whichever is highest
```

### Wrong-Date Selection
For each beneficiary, select the payment date they don't receive that is most distant from their actual date(s), using circular month distance.

### Panel Propagation
If someone reports a benefit in ANY wave → coded as beneficiary in ALL waves, unless they explicitly select "None" in a specific wave.

### Sample Restrictions
- Filter to `progress >= 80` (survey completion ≥80%)
- Note: `progress` is stored as character, must convert to numeric first
- Reduces sample from 12,117 to 11,262 observations

### Interaction Model Notes
- **Collinearity warning expected**: Time-invariant moderators (years_in_qc, income_filled) are collinear with individual FE. This is fine—the main effect of the moderator is absorbed, but the interaction term is still estimable.
- **Years in QC calculation**: `years_in_qc = 2023 - yearqc` (year arrived in Quebec from wave 1)
- **Household income coding**: 8-point scale from `hhincome` (1 = no income, 8 = >$200k). Missing values filled from other waves within individual.

---

## Workflow & Style Preferences

### Packages
- **Tables**: `modelsummary` with `tinytable` backend (set via `options(modelsummary_factory_default = "tinytable")`)
- **Models**: `fixest::feols()` for panel FE
- **Marginal effects**: `marginaleffects::slopes()` for interaction effect plots
- **Plots**: `ggthemes` — use `theme_tufte()` and `scale_color_few()` (hrbrthemes has font issues)
- **Data wrangling**: tidyverse

### Code Style
- **Models must be visible in code** — don't wrap model estimation in helper functions. Each `feols()` call should be explicit so I can see what's being estimated.
- **Quarto for analysis documents** — render directly rather than writing separate R scripts
- Keep data prep chunks hidden (`#| include: false`) but model chunks can show tables
- Use `#| label: tbl-*` and `@tbl-*` cross-references for paper-ready output

### Output
- PDF format for paper drafts
- Clean tables without excessive GOF stats (typically just `nobs`, `FE: ID`)
- Stars: `* p<0.1, ** p<0.05, *** p<0.01`

---

## Next Steps

- [x] Implement pooled beneficiary analysis
- [x] Develop wrong-date placebo methodology
- [x] Add paycheck placebo (non-beneficiaries)
- [x] Test origin country outcomes (H2)
- [x] Compare immigrant vs non-immigrant
- [x] Clean up document for paper format
- [x] Write Data & Methods section
- [x] Add balance checks (day of month ~ beneficiary; income ~ timing)
- [x] Create coefficient plot visualization (treatment vs placebo by DV)
- [x] Move detailed placebo tables to appendix
- [x] Add exclusive CCB recipient analysis (408 individuals, strongest results)
- [x] Add parent placebo (immigrants with kids but no CCB)
- [x] Add non-immigrant CCB comparison (228 individuals, null results)
- [x] Write up methods section with program details, payment amounts, and citations
- [x] Add heterogeneity analysis (interaction effects by years in QC, household income)
- [x] Add interaction model tables to appendix
- [x] Draft introduction with welfare chauvinism framing and cross-national examples
- [x] Add French competency, education, political knowledge, policy knowledge heterogeneity
- [x] Test generalized trust DVs (failed placebo — removed)
- [ ] Complete full paper introduction/lit review
- [ ] Robustness checks (different windows, controls)
- [ ] Coefficient interpretation (effect sizes)

---

## Visualization Notes

**Main coefficient plot** (`@fig-coef-plot`):
- Shows treatment (benefit payday) vs placebo (wrong date) for each DV
- Faceted by outcome, 3 columns
- Uses `theme_tufte()` + `scale_color_few()` from ggthemes
- Stars for significance displayed next to CI whiskers
- Legend: "Proximity to: Benefit Payday / Placebo Date"

**Interaction plots** (`@fig-interaction-*`):
- Show marginal effect of proximity (y-axis) across moderator values (x-axis)
- Uses `marginaleffects::slopes()` with `datagrid()` for prediction grid
- Single line per facet with 95% CI ribbon
- Dashed horizontal line at zero for reference
- Faceted by outcome (9 DVs), 3 columns
- Steelblue for years plots, darkgreen for income plots

---

## Introduction & Literature Review

**Framing**: The paper opens by noting that immigrant welfare use is politically contentious, then pivots to ask the under-studied reverse question: how does *receiving* benefits affect *immigrants'* political attitudes?

**Key literatures engaged**:
1. **Welfare chauvinism** — native preferences to restrict benefits to citizens [@ennserjedenastik2018; @careja2022]
2. **Immigration attitudes & welfare support** — anti-immigrant views reduce welfare support [@garand2017; @burgoon2021]
3. **Policy feedback** — how government programs shape political behavior [@campbell2012; @kumlin2014; @mettler2011; @soss1999; @pierson1993]
4. **Immigrant political socialization** — attitudes evolve post-arrival [@dinesen2012; @just2017; @superti2022]
5. **Credit attribution** — material benefits → political support [@healy2017]

**Cross-national examples of welfare chauvinism rhetoric**:
- **U.S.**: Trump "public charge" rule expansion (2019) — penalizes immigrants for using Medicaid, SNAP, housing [@trump_publiccharge2019; @mpi_publiccharge2024]
- **France**: Le Pen's *préférence nationale* — reserve benefits for French citizens [@lepen_preference2022]
- **UK**: Farage/UKIP "health tourism" claims — actual costs <0.1% of NHS budget [@farage_healthtourism2015; @king_healthtourism2015]

**Pro-integration argument**: OECD research shows settlement services (including welfare access) improve integration outcomes [@oecd_integration2023]

**Gap identified**: Large literature on native attitudes toward immigrant welfare use; almost no work on how benefit receipt shapes immigrants' own political attitudes. Existing work limited by: hard-to-survey population, endogeneity, cross-sectional designs.
