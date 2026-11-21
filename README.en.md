# Area KPI Control Platform

[Türkçe](README.md) | **English**

An Excel platform that consolidates sales, profitability, CRM, delivery, product mix, waste, inventory, training, turnover, guest complaints, and audit KPIs for a multi-store area into a **single colour-coded table** and assigns each store a **100-point performance score**.

> **Note:** This file is a **version rebuilt with synthetic data** of the platform I built and ran every month for a 16-store area at a coffee chain. The original ran on the company's SharePoint environment. The structure (source sheets, overview table, target row, period selector, performance score) matches the original. Store names, figures, and comments are synthetic.
>
> Performance score **weights are sample values**; in the live system each KPI carried its own weight. Target thresholds are taken from the target row of the original workbook.

## What problem it solves

A store's monthly performance is normally scattered across a dozen separate reports: sales, P&L, CRM, delivery platforms, waste and inventory, training completion, turnover, guest complaints, and audits. This platform:

- Places each source report on its own sheet and merges them by store + period key into one overview table.
- Compares every KPI against its target with green/red conditional formatting.
- Sums the weights of all KPIs meeting target to score and rank stores (used in the original operation as input to store manager performance reviews).
- Displays P&L variance explanations right beside each store row.

During the monthly area meeting, variances are reviewed directly from this table and store-level actions are assigned.

## Before

KPIs were tracked by opening separate emailed reports from different sources one by one.

## Sheets

| Sheet | Purpose |
|---|---|
| `Nasil_Kullanilir` | Monthly workflow, abbreviations, colour coding |
| `Genel_Tablo` | Period selector; one row per store across 21 indicators, target row, area row, score, rank, and P&L variance note |
| `Hedefler` | Direction (≥ / ≤), target threshold, and performance weight for each KPI |
| `Performans_Puani` | Per-KPI earned score matrix, total score, and chart |
| `Satis` · `PnL` · `CRM` · `Paket_Servis` · `Urun_Karmasi` · `Fire_Envanter` · `Egitim` · `Personel` · `Kahve_Sohbeti` · `Sikayet` · `Denetim` | Paste sheets for source system reports |

## Indicators and targets

| Group | Indicator | Formula | Target |
|---|---|---|---|
| Sales | Sales vs. budget variance | net sales ÷ budget − 1 | ≥ 0% |
| P&L | Store contribution (Line 12) vs. budget | (actual − budget) ÷ \|budget\| | ≥ 0% |
| CRM | CRM sales share | CRM sales ÷ net sales | ≥ 14% |
| Delivery | Cancellation rate | cancellations ÷ transactions (2 platforms) | ≤ 7% |
| Delivery | Platform online availability | average of 2 platforms | ≥ 90% |
| Product mix | Origin espresso share | origin espresso ÷ espresso beverages | ≥ 18% |
| Product mix | Food attach delta | (food ÷ beverage) − prior year | ≥ 0 |
| Waste | Food mark-out rate | mark-out ÷ food sales | ≤ 8% |
| Inventory | Inventory count variance | variance ÷ net sales | ≥ −0.5% |
| People | Training completion | completed ÷ assigned | ≥ 95% |
| People | Turnover | YTD leavers ÷ average headcount | ≤ 50% |
| People | Coffee tasting sessions delta | completed − (headcount × 0.2 × 2) | ≥ 0 |
| Guest | Complaint rate | complaints ÷ transactions × 1,000 | ≤ 0.30 |
| Audit | ASA (general operations) | latest audit score | ≥ 90 |
| Audit | PAP (loss prevention) | latest audit score | ≥ 85 |
| Audit | RSA (food safety) | latest audit score | ≥ 90 |

Store contribution (Line 12) is the bottom line of store P&L: net sales minus COGS, royalty, labour, controllable expenses, rent, and depreciation.

## Performance score

Each KPI awards its weight from `Hedefler` if it meets target, or 0 otherwise. Weights sum to 100 (the sheet alerts if the sum differs from 100). Indicators without data are excluded. On `Genel_Tablo`, scores ≥ 80 highlight green and < 60 highlight red.

## Usage

No macros or setup required. `bolge-kpi-platformu.xlsx` opens in Excel 2010+ and LibreOffice.

1. Each month, paste source reports into their respective sheets starting at **column B** (period code P1–P12, store name, report columns) and fill down the key formula in column A.
2. Select the period in `Genel_Tablo` > cell B1.
3. Review variances and rankings on `Genel_Tablo` and `Performans_Puani`.

The sample file includes periods P1–P3 and 8 stores.

## Adapting to your data

| Location | What to adjust |
|---|---|
| `Genel_Tablo` cols A–B | Store names and formats (must match source sheets) |
| `Hedefler` | Targets, directions, and weights |
| Source sheets | Column references in `Genel_Tablo` if source report column order differs |

To add stores, copy a row down on `Genel_Tablo` and `Performans_Puani` and extend the area summary ranges.

## Limitations

- Reports are pasted manually from source systems; there is no automated API pull.
- Actions are agreed live in meetings, so no separate action-log sheet is included.
- YTD figures apply only to turnover (as provided by the source report); all other indicators show monthly values.

## License

MIT. See `LICENSE` for details.
