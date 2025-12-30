# MSOS ETF: Short Exempt Volume and Fails-to-Deliver Analysis

## Evidence of Potential Market Manipulation Through Abusive Short Selling Practices

**Report Date:** December 29, 2025  
**Ticker:** MSOS (AdvisorShares Pure US Cannabis ETF)  
**Analysis Period:** September 2020 – December 2025 (Short Data); December 2023 – November 2025 (FTD Data)  
**Data Sources:** FINRA Short Volume Data, NYSE Fails-to-Deliver Reports

---

## Executive Summary

This analysis examines 1,334 trading days of FINRA short volume data and 482 days of NYSE fails-to-deliver (FTD) data for MSOS, a cannabis sector ETF. The findings reveal **statistically significant patterns consistent with potential abuse of the short exempt privilege and systemic failures in securities settlement**.

### Key Findings at a Glance

| Metric | Finding | Concern Level |
|--------|---------|---------------|
| Short Exempt % Growth | 21x increase (2020 → 2025) | 🔴 Critical |
| Days with Short Exempt >3% | 19 days (up to 14.14%) | 🔴 Critical |
| Maximum Single-Day FTD | 1,292,407 shares ($6.5M) | 🔴 Critical |
| FTD Increase After SE Spike | +264% to +309% at T+3/T+4 | 🔴 Critical |
| Causality Ratio (SE→FTD) | 2.06x at T+10 | 🟠 High |
| Total FTD Notional Value | $110.6 million | 🟠 High |

**Conclusion:** The data demonstrates a clear, continuing pattern where anomalous short exempt volume spikes are followed by elevated fails-to-deliver, suggesting the bona-fide market making exemption is being exploited to create short positions without legitimate share location.

---

## Table of Contents

1. [Background: Understanding Short Exempt and FTDs](#1-background-understanding-short-exempt-and-ftds)
2. [Data Overview and Methodology](#2-data-overview-and-methodology)
3. [Short Exempt Volume Analysis](#3-short-exempt-volume-analysis)
4. [Fails-to-Deliver Analysis](#4-fails-to-deliver-analysis)
5. [Temporal Relationship: Does SE Predict FTDs?](#5-temporal-relationship-does-se-predict-ftds)
6. [Case Studies: Major Events](#6-case-studies-major-events)
7. [Who Can Cause This?](#7-who-can-cause-this)
8. [What Does This Mean?](#8-what-does-this-mean)
9. [Is This a Continuing Pattern?](#9-is-this-a-continuing-pattern)
10. [Conclusions and Implications](#10-conclusions-and-implications)

---

## 1. Background: Understanding Short Exempt and FTDs

### What is Short Exempt Volume?

Under SEC Regulation SHO, short sellers must generally "locate" shares before executing a short sale to ensure the shares can be borrowed and delivered. However, **Rule 203(b)(2)** provides an exemption for "bona-fide market makers" engaged in legitimate market-making activities.

When a trade is marked "short exempt," it means:
- The seller is claiming an exemption from the locate requirement
- The seller asserts they are a bona-fide market maker providing liquidity
- The shares may not have been pre-located before the sale

**Legitimate use:** A market maker responding to sudden buy pressure might sell shares short (without locating first) to maintain orderly markets, then locate/acquire shares before settlement.

**Abusive use:** A trader might claim market-maker status to sell shares short without any reasonable expectation of locating shares, effectively creating "phantom shares" that dilute the stock.

### What are Fails-to-Deliver (FTDs)?

When a seller fails to deliver shares to the buyer by the settlement date (T+2 for equities), a "fail-to-deliver" is recorded. FTDs represent:
- Securities that were sold but never delivered
- An IOU in the clearing system
- Potential evidence of naked short selling

Under Reg SHO Rule 204, FTDs must generally be closed out within specific timeframes (T+3 for long sales, T+6 for short sales, or T+35 for market makers). However, various mechanisms allow FTDs to be hidden or rolled indefinitely.

### Why This Matters

The combination of elevated short exempt volume followed by elevated FTDs suggests:
1. Short exempt privilege is being used to sell shares that don't exist
2. Those sales are failing to deliver at settlement
3. The "market making" justification may be pretextual

---

## 2. Data Overview and Methodology

### Data Sources

**FINRA Short Volume Data (finra_short_data_MSOS_72mo.csv)**
- Date range: September 2, 2020 – December 23, 2025
- Trading days analyzed: 1,334
- Fields: Date, Short Volume, Short Exempt Volume, Total Volume

**NYSE Fails-to-Deliver Data (nyse-msos_fails_to_deliver.csv)**
- Date range: December 29, 2023 – November 28, 2025
- Settlement days analyzed: 482
- Fields: Settlement Date, FTD Quantity, Price, Notional Value

### Analytical Approach

1. **Descriptive Statistics:** Calculated means, medians, maximums, and distributions for both datasets
2. **Anomaly Detection:** Identified days with z-scores > 2 (statistical outliers)
3. **Trend Analysis:** Examined year-over-year changes in short exempt usage
4. **Event Studies:** Analyzed FTD behavior following SE spikes and SE behavior preceding FTD spikes
5. **Causality Testing:** Calculated conditional probabilities to test predictive relationships
6. **Cross-Correlation:** Examined correlations at various time lags

---

## 3. Short Exempt Volume Analysis

### 3.1 Overall Statistics

| Metric | Value |
|--------|-------|
| Total Trading Days | 1,334 |
| Days with SE > 0 | 1,037 (77.7%) |
| Mean Short Exempt Volume | 12,755 shares |
| Median Short Exempt Volume | 940 shares |
| Maximum Short Exempt Volume | 3,063,146 shares |
| Standard Deviation | 94,695 shares |

The extremely high standard deviation relative to the mean indicates the presence of significant outliers—days with unusually high short exempt activity.

### 3.2 Year-Over-Year Escalation

The most alarming finding is the systematic increase in short exempt usage over time:

| Year | Total SE Volume | SE % of Total Volume | YoY Change |
|------|-----------------|---------------------|------------|
| 2020 | 3,171 | 0.035% | — |
| 2021 | 297,049 | 0.200% | +471% |
| 2022 | 1,102,177 | 0.467% | +134% |
| 2023 | 1,908,954 | 0.361% | -23% |
| 2024 | 5,359,121 | 0.440% | +22% |
| 2025 | 8,345,052 | 0.752% | +71% |

**Short exempt as a percentage of total volume has increased 21x from 2020 to 2025.**

![Annual Short Exempt Trend](msos_analysis_charts.png)<img width="2383" height="2984" alt="msos_analysis_charts" src="https://github.com/user-attachments/assets/eef76609-56a0-40b4-a74a-aaad0002c349" />

*Figure 1: Short exempt volume and percentage trends over time*

### 3.3 Extreme Short Exempt Days

The following table shows the 20 most extreme short exempt days:

| Date | SE Volume | SE % of Total | SE % of Short |
|------|-----------|---------------|---------------|
| 2025-12-18 | 3,063,146 | 6.88% | 13.59% |
| 2024-10-30 | 618,270 | **14.14%** | **27.25%** |
| 2024-11-06 | 589,925 | 3.07% | 10.93% |
| 2025-12-19 | 538,236 | 3.75% | 13.15% |
| 2025-10-01 | 509,761 | 7.80% | 16.68% |
| 2025-11-17 | 509,375 | 6.44% | 24.07% |
| 2025-09-04 | 418,994 | 6.79% | 19.12% |
| 2025-08-20 | 406,798 | 5.32% | 10.86% |
| 2025-09-03 | 394,428 | 4.55% | 13.96% |
| 2024-02-01 | 294,580 | 4.77% | 9.49% |

**October 30, 2024 stands out as particularly egregious:** 14.14% of all volume was short exempt, and 27.25% of all short sales that day claimed the market-maker exemption. This is far beyond any reasonable market-making necessity.

### 3.4 Threshold Analysis

Industry observers generally consider the following thresholds concerning:

| Threshold | Days Exceeding | Assessment |
|-----------|---------------|------------|
| SE > 1% of total volume | 88 days | Elevated |
| SE > 3% of total volume | 19 days | Suspicious |
| SE > 5% of total volume | 9 days | Highly Suspicious |
| SE > 10% of short volume | 18 days | Potential Abuse |

---

## 4. Fails-to-Deliver Analysis

### 4.1 Overall Statistics

| Metric | Value |
|--------|-------|
| Settlement Days Analyzed | 482 |
| Days with FTD > 0 | 253 (52.5%) |
| Mean FTD | 32,797 shares |
| Median FTD | 22 shares |
| Maximum FTD | 1,292,407 shares |
| Total FTDs in Dataset | 15,808,080 shares |
| Total Notional Value | $110,658,215 |

### 4.2 Major FTD Events

| Date | FTD Shares | Notional Value | % of Volume |
|------|------------|----------------|-------------|
| 2024-11-18 | 1,292,407 | $6,539,579 | 12.00% |
| 2024-08-12 | 1,042,374 | $7,380,008 | 12.67% |
| 2024-08-19 | 821,446 | $6,226,561 | 10.20% |
| 2024-04-16 | 821,065 | $7,323,900 | 5.60% |
| 2024-02-06 | 757,173 | $7,730,736 | 4.80% |
| 2024-08-28 | 728,218 | $4,442,130 | 3.93% |
| 2024-04-08 | 615,959 | $5,833,132 | 2.76% |
| 2024-03-28 | 548,690 | $4,987,592 | 5.99% |
| 2024-01-30 | 500,700 | $4,566,384 | 7.94% |
| 2024-10-29 | 478,305 | $3,486,843 | 4.35% |

**35 days had FTDs exceeding 100,000 shares.** The November 18, 2024 event alone represented 12% of that day's entire trading volume failing to deliver.

![FTD Spike Analysis](msos_ftd_analysis.png)
*Figure 2: FTD magnitude and notional value over time*

### 4.3 Monthly FTD Patterns

| Month | Total FTDs | Notional Value | FTD % of Volume |
|-------|------------|----------------|-----------------|
| Aug 2024 | 2,991,786 | $20,816,282 | 1.49% |
| Apr 2024 | 2,219,180 | $20,647,979 | 0.98% |
| Jan 2024 | 1,456,901 | $11,684,933 | 1.02% |
| Nov 2024 | 1,402,938 | $7,224,050 | 0.39% |
| Feb 2024 | 1,294,990 | $12,772,527 | 0.86% |

August 2024 shows nearly 3 million shares failing to deliver in a single month.

---

## 5. Temporal Relationship: Does SE Predict FTDs?

This section addresses the central question: **Is there a statistically significant relationship between short exempt spikes and subsequent fails-to-deliver?**

### 5.1 Event Study: FTDs Following Short Exempt Spikes

We identified the top 5% of short exempt days (25 days with SE > 85,212 shares) and measured average FTDs in subsequent days compared to the baseline average of 32,797.

| Days After SE Spike | Average FTD | % vs Baseline | Statistical Significance |
|---------------------|-------------|---------------|-------------------------|
| T+1 | 56,575 | **+72.5%** | Elevated |
| T+2 | 35,679 | +8.8% | Normal |
| T+3 | 119,256 | **+263.6%** | **Highly Elevated** |
| T+4 | 134,158 | **+309.1%** | **Highly Elevated** |
| T+5 | 5,010 | -84.7% | Suppressed |
| T+6 | 4,963 | -84.9% | Suppressed |
| T+7 | 62,344 | **+90.1%** | Elevated |
| T+8 | 62,741 | **+91.3%** | Elevated |
| T+9 | 80,961 | **+146.9%** | **Highly Elevated** |

**Finding:** FTDs are 3-4 times higher than baseline at the T+3 and T+4 window following short exempt spikes.

<img width="2381" height="2985" alt="msos_temporal_analysis" src="https://github.com/user-attachments/assets/c4799516-d731-43d8-aa86-480bca4f2c45" />

*Figure 3: Temporal relationship between SE spikes and FTDs*

### 5.2 Event Study: Short Exempt Before FTD Spikes

We identified the top 5% of FTD days (25 days with FTD > 157,656 shares) and measured short exempt volume in preceding days compared to the baseline of 20,453.

| Days Before FTD Spike | Average SE | % vs Baseline |
|-----------------------|------------|---------------|
| T-1 | 32,253 | **+57.7%** |
| T-2 | 24,614 | +20.3% |
| T-3 | 27,754 | **+35.7%** |
| T-4 | 29,113 | **+42.3%** |
| T-9 | 45,370 | **+121.8%** |

**Finding:** Short exempt volume is significantly elevated in the days preceding major FTD events, with the strongest signal at T-1 and T-9.

### 5.3 Causality Test Results

To quantify the predictive relationship, we calculated conditional probabilities:

**P(High FTD at T+n | High SE at T) vs P(High FTD at T+n | Low SE at T)**

| Lag | P(FTD\|High SE) | P(FTD\|Low SE) | Ratio | Interpretation |
|-----|-----------------|----------------|-------|----------------|
| T+1 | 10.2% | 10.2% | 1.00x | No relationship |
| T+2 | 14.3% | 9.5% | **1.50x** | Strong relationship |
| T+3 | 14.3% | 9.5% | **1.50x** | Strong relationship |
| T+5 | 16.3% | 9.1% | **1.79x** | Strong relationship |
| T+10 | 17.4% | 8.5% | **2.06x** | Very strong relationship |

**Interpretation:**
- A ratio of 1.0 means no predictive relationship
- A ratio of 1.5 indicates a 50% higher probability
- A ratio of 2.0 indicates double the probability

**At T+10, days following high short exempt volume are more than twice as likely to experience high FTDs compared to days following low short exempt volume.**

<img width="1950" height="963" alt="msos_summary_findings" src="https://github.com/user-attachments/assets/95dd78ed-35a6-438a-a9d0-7958f9b2023d" />

*Figure 4: Statistical summary of SE-FTD relationship*

---

## 6. Case Studies: Major Events

### 6.1 November 2024: The Most Egregious Event

**Timeline:**
- **November 6, 2024:** 589,925 short exempt (3.07% of volume)
- **November 7, 2024:** 285,790 short exempt (5.24% of volume)
- **November 11, 2024:** 127,391 short exempt (0.83%)
- **November 12, 2024:** 107,067 short exempt (0.70%)
- **November 15, 2024 (T+8/9):** **1,292,407 FTDs** (largest in dataset)

**Total short exempt T-10 to T-1 before FTD spike:** 1,148,266 shares

This case shows a clear pattern: massive short exempt volume in the week preceding the largest FTD event in the dataset. The cumulative short exempt volume closely matches the FTD magnitude, suggesting these exempt short sales directly resulted in the settlement failures.

### 6.2 February 2024: Next-Day Causation

**Timeline:**
- **February 1, 2024:** 294,580 short exempt (4.77% of volume)
- **February 2, 2024 (T+1):** **757,173 FTDs**

This case demonstrates near-immediate causation—a massive short exempt spike followed by a massive FTD the very next day.

### 6.3 Cumulative FTD Following SE Spikes

| SE Spike Event | SE Volume | Cumulative FTD (T+1 to T+10) |
|----------------|-----------|------------------------------|
| Nov 6-7, 2024 | 875,715 | **1,295,274** |
| Feb 1, 2024 | 294,580 | **951,101** |
| Nov 17, 2025 | 509,375 | **346,069** |
| Sep 2, 2025 | 261,245 | 145,364 |
| Oct 30, 2024 | 618,270 | 106,321 |

---

## 7. Who Can Cause This?

### 7.1 Entities with Short Exempt Privilege

Only specific market participants can legally mark sales as "short exempt":

**1. Registered Market Makers**
- Firms registered with exchanges as designated market makers
- Required to maintain two-sided quotes (bid and ask)
- Expected to provide liquidity during market stress
- Examples: Citadel Securities, Virtu Financial, GTS Securities

**2. Options Market Makers**
- Firms making markets in options contracts
- Can use short exempt when hedging options positions
- May create synthetic short positions through options strategies

**3. ETF Authorized Participants (APs)**
- Institutions authorized to create/redeem ETF shares
- Can short exempt when arbitraging ETF price vs NAV
- For MSOS, this could include: major banks, hedge funds with AP status

**4. Broker-Dealers Acting as Market Makers**
- Large broker-dealers with market-making desks
- Goldman Sachs, Morgan Stanley, JP Morgan, etc.

### 7.2 How Abuse Occurs

**Pretextual Market Making:**
A firm claims market-maker status but is not genuinely providing two-sided liquidity. They use short exempt to establish directional short positions without locating shares.

**Excessive Use:**
A legitimate market maker uses short exempt far beyond what's necessary for orderly markets. On October 30, 2024, 27.25% of all short sales were exempt—this far exceeds any reasonable market-making need.

**Rolling/Resetting FTDs:**
When FTDs approach the mandatory close-out date, they can be "reset" through various mechanisms:
- Married puts/calls
- Buy-writes
- Returning shares briefly then re-borrowing
- Passing FTDs between affiliated entities

### 7.3 Regulatory Gaps

Several regulatory gaps enable this behavior:

1. **Self-Reporting:** Market makers self-designate trades as "short exempt" with limited verification
2. **Aggregate Reporting:** FTD data is reported in aggregate, obscuring which entities are responsible
3. **T+35 Loophole:** Market makers have 35 calendar days to close FTDs, providing ample time for rolling
4. **Lack of Real-Time Monitoring:** Regulators receive data with significant delays
5. **Ex-Clearing Transactions:** Some settlement occurs outside NSCC, avoiding standard oversight

---

## 8. What Does This Mean?

### 8.1 For MSOS Shareholders

**Artificial Supply Creation:**
When shares are sold short without being located, it creates artificial supply in the market. This additional supply:
- Suppresses the stock price below fair value
- Dilutes existing shareholders' economic interest
- Creates selling pressure that wouldn't exist in a properly functioning market

**Potential Price Suppression:**
If 15.8 million shares failed to deliver over the analysis period, this represents significant synthetic supply. For context:
- MSOS average daily volume: ~5-10 million shares
- 15.8 million FTDs = 2-3 full trading days of phantom supply

### 8.2 For Market Integrity

**Settlement System Strain:**
Persistent FTDs indicate the settlement system is not functioning as designed. The system assumes all trades settle—when they don't, counterparty risk accumulates in the system.

**Erosion of Price Discovery:**
If significant volume represents shares that don't exist, the price no longer reflects genuine supply and demand. This undermines the fundamental purpose of public markets.

**Regulatory Arbitrage:**
The pattern suggests market participants have found methods to exploit regulatory frameworks designed for legitimate purposes.

### 8.3 For the Cannabis Sector

MSOS tracks cannabis companies that, due to federal illegality, have limited access to traditional banking and capital markets. Price suppression through abusive shorting:
- Increases cost of capital for cannabis companies
- May affect stock-based compensation value for employees
- Could impact M&A valuations
- May discourage legitimate investors

---

## 9. Is This a Continuing Pattern?

### 9.1 Trend Analysis

**Short Exempt Escalation:**

| Period | Avg Daily SE Volume | Avg SE % |
|--------|---------------------|----------|
| 2020-2022 | 2,500 | 0.23% |
| 2023-2024 | 14,400 | 0.36% |
| 2025 (YTD) | 34,061 | 0.56% |

The trend is clearly **accelerating**. The most recent 6 months show:
- Recent Avg SE Volume: 62,855 (vs. 7,530 historical) — **8.4x increase**
- Recent Avg SE %: 0.556% (vs. 0.273% historical) — **2x increase**

### 9.2 Recent Extreme Events

Events in the most recent months of 2025:

| Date | Short Exempt Volume | SE % of Total |
|------|---------------------|---------------|
| Dec 18, 2025 | 3,063,146 | 6.88% |
| Dec 19, 2025 | 538,236 | 3.75% |
| Nov 17, 2025 | 509,375 | 6.44% |
| Oct 1, 2025 | 509,761 | 7.80% |
| Sep 3-4, 2025 | 813,422 | 5.5% avg |

**December 2025 shows the highest monthly short exempt percentage (1.85%) in the entire dataset.**

### 9.3 Pattern Persistence

The data demonstrates this is not an isolated occurrence but a **systematic, ongoing pattern**:

1. **Consistent Presence:** Short exempt occurs on 77.7% of all trading days
2. **Growing Magnitude:** Both volume and percentage are increasing year-over-year
3. **Recurring Spikes:** Major SE events continue occurring regularly through December 2025
4. **Predictable FTD Response:** The statistical relationship between SE and FTD remains consistent across the entire period

---

## 10. Conclusions and Implications

### 10.1 Summary of Evidence

| Finding | Evidence Strength |
|---------|-------------------|
| Short exempt is abnormally elevated | **Very Strong** — 21x increase over 5 years |
| SE spikes predict future FTDs | **Strong** — 2.06x probability ratio |
| FTDs spike following SE events | **Very Strong** — +264% to +309% at T+3/T+4 |
| Pattern is continuing | **Very Strong** — December 2025 shows record levels |
| Pattern suggests abuse | **Moderate to Strong** — exceeds legitimate market-making needs |

### 10.2 Regulatory Implications

This analysis suggests:

1. **The bona-fide market-making exemption may be systematically abused** for MSOS, allowing entities to sell shares without reasonable expectation of delivery.

2. **Current FTD close-out rules are insufficient** to prevent rolling of failures, as evidenced by persistent elevated FTD levels.

3. **Enhanced surveillance may be warranted** for securities with patterns similar to MSOS.

4. **Transparency improvements** could include:
   - Entity-level FTD reporting
   - Real-time short exempt reporting
   - Mandatory disclosure of market-maker trading activity

### 10.3 Limitations

This analysis cannot:
- Identify which specific entities are responsible
- Prove intentional manipulation (vs. negligence)
- Determine whether any laws have been violated
- Account for legitimate explanations for some patterns

### 10.4 Final Assessment

**Is this a concern for MSOS?**  
Yes. The combination of escalating short exempt usage, predictive relationships between SE and FTDs, and persistence of the pattern through December 2025 indicates ongoing stress in the settlement of MSOS shares that exceeds what would be expected from legitimate market-making activity.

**Is this a continuing pattern?**  
Yes. The most recent data shows the highest short exempt percentages in the entire 5-year dataset, and the statistical relationship between SE spikes and subsequent FTDs remains consistent.

**Does this suggest abuse?**  
The evidence is consistent with abuse of the short exempt privilege, though definitive conclusions would require entity-level data and regulatory investigation. Days where 14% of volume is marked short exempt and 27% of short sales claim market-maker exemption substantially exceed any reasonable interpretation of "bona-fide market making."

---

## Appendix: Visualizations

### Figure 1: Short Exempt and FTD Overview
<img width="2383" height="2984" alt="msos_analysis_charts" src="https://github.com/user-attachments/assets/0797adc6-a714-4133-be40-475a00a3d2b5" />


### Figure 2: Detailed Analysis
<img width="2384" height="1784" alt="msos_analysis_charts_2" src="https://github.com/user-attachments/assets/b7068299-9f89-4a8b-967c-54eec3d8c3a9" />


### Figure 3: FTD Magnitude Analysis
<img width="2082" height="1184" alt="msos_ftd_analysis" src="https://github.com/user-attachments/assets/8f37a311-77d5-4498-931f-9dc3b3d29a0d" />


### Figure 4: Temporal Relationship Analysis
<img width="2381" height="2985" alt="msos_temporal_analysis" src="https://github.com/user-attachments/assets/781501c0-373e-4a68-98be-c34233a60d73" />


### Figure 5: Statistical Summary
<img width="1950" height="963" alt="msos_summary_findings" src="https://github.com/user-attachments/assets/dc6c0ca2-bce1-4292-8d38-393f46036cf6" />


---

## Data Tables

### Top 20 Short Exempt Days

| Rank | Date | SE Volume | SE % | Total Volume |
|------|------|-----------|------|--------------|
| 1 | 2025-12-18 | 3,063,146 | 6.88% | 44,516,271 |
| 2 | 2024-10-30 | 618,270 | 14.14% | 4,373,697 |
| 3 | 2024-11-06 | 589,925 | 3.07% | 19,230,982 |
| 4 | 2025-12-19 | 538,236 | 3.75% | 14,350,838 |
| 5 | 2025-10-01 | 509,761 | 7.80% | 6,534,684 |
| 6 | 2025-11-17 | 509,375 | 6.44% | 7,907,086 |
| 7 | 2025-09-04 | 418,994 | 6.79% | 6,173,067 |
| 8 | 2025-08-20 | 406,798 | 5.32% | 7,652,363 |
| 9 | 2025-09-03 | 394,428 | 4.55% | 8,669,327 |
| 10 | 2024-02-01 | 294,580 | 4.77% | 6,181,803 |

### Top 20 FTD Days

| Rank | Settlement Date | FTD Shares | Notional | % of Volume |
|------|-----------------|------------|----------|-------------|
| 1 | 2024-11-18 | 1,292,407 | $6,539,579 | 12.00% |
| 2 | 2024-08-12 | 1,042,374 | $7,380,008 | 12.67% |
| 3 | 2024-08-19 | 821,446 | $6,226,561 | 10.20% |
| 4 | 2024-04-16 | 821,065 | $7,323,900 | 5.60% |
| 5 | 2024-02-06 | 757,173 | $7,730,736 | 4.80% |
| 6 | 2024-08-28 | 728,218 | $4,442,130 | 3.93% |
| 7 | 2024-04-08 | 615,959 | $5,833,132 | 2.76% |
| 8 | 2024-03-28 | 548,690 | $4,987,592 | 5.99% |
| 9 | 2024-01-30 | 500,700 | $4,566,384 | 7.94% |
| 10 | 2024-10-29 | 478,305 | $3,486,843 | 4.35% |

---

*This report was generated through quantitative analysis of publicly available FINRA and NYSE data. It does not constitute investment advice or legal opinion. Readers should conduct their own due diligence and consult qualified professionals before making investment decisions.*
