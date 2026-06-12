# CB Upsell Helper

A self-contained, browser-based sales tool for Carbon Black Cloud reps to identify upsell opportunities. No server, no build step, no dependencies — just open the HTML file.

---

## What It Does

Guides you through a 4-step workflow to generate intelligent upsell recommendations based on:

1. **Cloud posture** — Cloud Friendly vs. Cloud Adverse
2. **Current products** the customer already owns
3. **Clarifying questions** that appear dynamically based on selections
4. **Recommendations** with SKU codes and business justification

The recommendation engine deduplicates, supersedes lower-tier suggestions with higher-tier ones, and consolidates overlapping products (e.g., Workloads Foundations + Enterprise EDR → Workloads Enterprise).

---

## Usage

Open `CB Upsell Helper - v1.2.html` in any modern browser. No installation required.

---

## Products Covered

**Endpoint Bundles**
- Endpoint Foundations — NGAV + Basic Behavioral EDR
- Endpoint Advanced — Foundations + Live Query + Vulnerability Management
- Endpoint Enterprise — Advanced + Enterprise EDR

**Workloads Bundles**
- Workloads Foundations — vCenter, AWS, Lifecycle Mgmt, Asset Inventory, Vuln Mgmt, Live Query
- Workloads Advanced — Foundations + NGAV
- Workloads Enterprise — Advanced + Enterprise EDR

**Individual Cloud Products**
- Enterprise EDR (standalone)
- Live Query (Audit & Remediation)
- Host-Based Firewall
- Endpoint NDR (eNDR/XDR)

**On-Premises**
- Carbon Black Response (EDR)
- App Control (legacy/POS systems)

---

## Key Logic

- **One bundle per family** — selecting a new Endpoint or Workloads bundle deselects the previous one
- **Bundle coverage** — selecting a bundle that includes a standalone product (e.g., Live Query) auto-deselects that product
- **Tier-matching** — if a customer has Endpoint Foundations, the minimum Workloads recommendation is Advanced for protection parity
- **Superseding** — higher-tier recommendations remove redundant lower-tier ones
- **Consolidation** — overlapping suggestions are combined into a single higher-tier product

---

## Files

| File | Description |
|---|---|
| `CB Upsell Helper - v1.2.html` | Current version — open this |
| `design.md` | Product logic, question triggers, and recommendation rules |
| `Archive/` | Previous versions (v1.0, v1.1) |

---

## Tech

Pure HTML/CSS/Vanilla JS. No framework, no build tooling, no external dependencies. Works offline and can be shared by email or hosted anywhere.
