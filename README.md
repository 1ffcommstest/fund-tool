[README.md](https://github.com/user-attachments/files/28512959/README.md)
# Luxembourg Fund Vehicle Selector

An interactive decision tool that guides asset managers and investors to the most appropriate Luxembourg investment vehicle for their strategy, investor base, and regulatory requirements.

Built and maintained by [Luxembourg for Finance](https://www.luxembourgforfinance.com) — the Agency for the Development of the Financial Centre.

---

## Purpose

Luxembourg offers one of the most comprehensive investment vehicle toolboxes in the world. Choosing the right structure depends on multiple intersecting factors: investor type, asset class, regulatory appetite, and speed to market.

This tool walks users through a short decision tree — typically 3–4 questions — and returns a recommended vehicle with key specifications, including regulatory status, time to market, eligible assets, subscription tax, and EU passporting options.

It is embedded as an iframe within Luxembourg for Finance's Foleon publications.

---

## Vehicles Covered

| Vehicle | Full Name | Type |
|---|---|---|
| UCITS | Undertaking for Collective Investment in Transferable Securities | Regulated |
| Part II UCI | Undertaking for Collective Investment (Part II) | Regulated |
| SIF | Specialised Investment Fund | Regulated AIF |
| SICAR | Société d'Investissement en Capital à Risque | Regulated AIF |
| RAIF | Reserved Alternative Investment Fund | Unregulated (AIFM-supervised) |
| SLP / SCSp | Special Limited Partnership | Unregulated |
| SOPARFI | Société de Participations Financières | Holding / Unregulated |
| SPF | Société de Gestion de Patrimoine Familial | Wealth Management |

---

## How It Works

The tool is a single self-contained HTML file (`index.html`) with no external dependencies beyond Google Fonts. All logic, styling, and data are inline.

The decision tree branches as follows:

```
Investor type
├── Retail
│   ├── Transferable securities → UCITS
│   └── Broader assets → Part II UCI
├── Professional / Well-informed
│   ├── Private equity
│   │   ├── Regulated → SICAR (concentrated) / SIF (diversified)
│   │   └── Fast launch → RAIF (with passport) / SLP (without)
│   ├── Real estate → SIF or RAIF
│   ├── Hedge / multi-strategy → SIF or RAIF
│   └── Multi-asset alternatives → SIF or RAIF
└── Private wealth / family
    ├── Passive family wealth → SPF
    └── Active holding / group → SOPARFI
```

---

## Deployment

This tool is deployed via GitHub Pages and served at:

```
https://[username].github.io/fund-tool/
```

It is embedded in Foleon documents via an iframe embed element. No build process or server-side logic is required — it is a static file.

---

## Updating Content

All vehicle data and decision tree logic is contained in two JavaScript objects at the top of the `<script>` block in `index.html`:

- **`VEHICLES`** — contains the name, description, specs, and alternative suggestions for each vehicle
- **`TREE` / `NODES`** — contains the decision tree questions, options, and branching logic

To update a vehicle's details (e.g. a change in minimum investment threshold or subscription tax rate), locate the relevant entry in `VEHICLES` and update the `specs` array.

To add a new decision branch, add a new node object to `NODES` and reference it from an existing option's `next` property.

---

## Data Sources

Vehicle specifications are based on:

- [ALFI — Luxembourg Investment Vehicles Guide (2019, updated)](https://www.alfi.lu)
- [Luxembourg for Finance — Asset Management Brochure (2023)](https://www.luxembourgforfinance.com)
- [CSSF — Commission de Surveillance du Secteur Financier](https://www.cssf.lu)
- [Chambers and Partners — Investment Funds Luxembourg 2025](https://practiceguides.chambers.com)
- Luxembourg Law of 21 July 2023 (fund toolbox modernisation)

> **Note:** Investment thresholds were updated by the Law of 21 July 2023, reducing the minimum investment for well-informed investors in SIFs, SICARs, and RAIFs from €125,000 to €100,000.

---

## Disclaimer

This tool is intended for informational purposes only and does not constitute legal, tax, or investment advice. Users should consult a qualified Luxembourg legal or financial adviser before making structuring decisions.

---

## Maintenance

| Item | Owner |
|---|---|
| Content accuracy | Luxembourg for Finance communications team |
| Technical updates | Web / digital team |
| Regulatory updates | To be reviewed annually or upon material law changes |

Last reviewed: June 2026
