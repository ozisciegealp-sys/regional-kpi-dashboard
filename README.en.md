# Area KPI Control Platform

[Türkçe](README.md) | **English**

An Excel platform that consolidates sales, P&L profitability, CRM, delivery platforms, product mix, waste, inventory variance, training, turnover, guest complaints, and audit results for a multi-store area into a **single colour-coded table**, scores each store out of **100 points**, and tracks cumulative ** League (`Yildizlar_Ligi`)** standings across periods.

> **Confidentiality & Synthetic Data Note:** This workbook is a **working version rebuilt entirely with synthetic data** of the online Excel platform I built and ran monthly for a 16-store area. All brand names, store identifiers, and company financials have been removed for confidentiality; the sample workbook models 8 synthetic stores (`Mağaza A`–`Mağaza H`) across 3 periods (`P1`–`P3`).

## What problem it solves

A store's monthly performance is typically scattered across a dozen separate reports: sales, P&L, CRM, delivery aggregators, waste/mark-out, inventory counts, training completion, HR turnover, guest complaints, and audits. This platform:

- Places all 11 source exports on dedicated tabs and merges them via a `Period|Store` key into one overview table.
- Benchmarks **16 scored operational KPIs** against target thresholds with green/red conditional formatting alongside **5 unscored context indicators** (`ADT`, `Net Sales`, `Store Contribution TL`, `Delivery Share %`, `Food Attach %` — 21 indicator columns in total).
- Sums the weights of achieved KPIs to score and rank stores out of 100.
- Tracks multi-period cumulative standings, store revenue tiers (`Tier 1–3`), month-over-month momentum, and league brackets (`Gold / Silver / Development League`) on **`Yildizlar_Ligi`**.
- Surfaces P&L variance notes right next to each store row to drive monthly store-level action plans.

## Before

Indicators were reviewed one by one across separate emailed spreadsheets and PDFs from different departments.

## Sheets

| Sheet | Purpose |
|---|---|
| `Nasil_Kullanilir` | Monthly workflow, abbreviations, and colour coding |
| `Genel_Tablo` | Period selector (`P1–P12`); one row per store across 16 scored KPIs + 5 context metrics (21 columns), target row, area summary, score, rank, and P&L variance note |
| `Performans_Puani` | Per-KPI earned score matrix for the selected period, total score, and bar chart |
| `Yildizlar_Ligi` | Multi-period (`P1–P3`) score trend, cumulative average, revenue tier (`Tier 1–3`), league bracket, cumulative sales/profitability, and chart |
| `Hedefler` | Direction (`≥` / `≤`), target threshold, and 100-point weights for all 16 scored KPIs |
| `Satis` · `PnL` · `CRM` · `Paket_Servis` · `Urun_Karmasi` · `Fire_Envanter` · `Egitim` · `Personel` · `Kahve_Sohbeti` · `Sikayet` · `Denetim` | 11 source data paste tabs |

## 16 Scored KPIs and sample targets

| Group | Indicator | Formula | Target |
|---|---|---|---|
| Sales | Sales vs. budget variance | net sales ÷ budget − 1 | ≥ 0.0% |
| P&L | Store contribution (Line 12) vs. budget | (actual − budget) ÷ \|budget\| | ≥ 0.0% |
| CRM | CRM sales share | CRM sales ÷ net sales | ≥ 14.0% |
| Delivery | Cancellation rate | cancellations ÷ transactions (2 platforms) | ≤ 7.0% |
| Delivery | Platform availability | average online availability (2 platforms) | ≥ 90.0% |
| Product mix | Origin espresso share | origin espresso ÷ espresso beverages | ≥ 18.0% |
| Product mix | Food attach YoY delta | (food ÷ beverage) − prior year | ≥ 0.0% |
| Waste | Food mark-out rate | mark-out ÷ food sales | ≤ 8.0% |
| Inventory | Inventory count variance | count variance ÷ net sales | ≥ −0.50% |
| People | Training completion | completed ÷ assigned | ≥ 95% |
| People | Turnover (YTD) | YTD leavers ÷ average headcount | ≤ 50% |
| People | Team check-in / tasting delta | completed − period target | ≥ 0 |
| Guest | Complaint rate | complaints ÷ transactions × 1,000 | ≤ 0.30 |
| Audit | ASA (general operations) | latest audit score | ≥ 90 |
| Audit | PAP (loss prevention) | latest audit score | ≥ 85 |
| Audit | RSA (food safety) | latest audit score | ≥ 90 |

## Usage

Macro-free; `bolge-kpi-platformu.xlsx` opens directly in Excel 2010+ and LibreOffice.

1. Paste monthly source reports starting at **column B** on each data tab and fill down the key formula in column A (`=B2&"|"&C2`).
2. Select the period (`P1`, `P2`, `P3`…) in `Genel_Tablo` > cell `B1`.
3. Review monthly variances on `Genel_Tablo` / `Performans_Puani` and cumulative standings on `Yildizlar_Ligi`.

## License

MIT. See `LICENSE` for details.
