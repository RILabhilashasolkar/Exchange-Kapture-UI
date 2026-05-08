# Kapture Exchange UI Prototype

A UI prototype for exchange-related fields on the Kapture CRM ticketing system used by Reliance Digital call centre agents.

## Live Preview

[https://rilabhilashasolkar.github.io/Exchange-Kapture-UI/kapture-exchange-ui.html](https://rilabhilashasolkar.github.io/Exchange-Kapture-UI/kapture-exchange-ui.html)

## Overview

This prototype extends the existing Kapture Orders tab with exchange-specific sections, enabling agents to handle exchange-related customer calls without switching systems.

The UI surfaces when `exchange_availed = true` OR `exchange_eligibility = true`.

## What's New

### 1. Exchange Status Strip
A quick-glance summary at the top of the Orders panel showing 4 status chips:
- Exchange Availed
- Exchange Status
- QC Decision
- Refund Status

### 2. Exchange Summary *(new section)*
All mandatory exchange fields in one place:
- Exchange Eligibility / Availed (True/False)
- Exchange Status
- Child Order ID
- Product Brand & Variant
- IMEI Captured (Yes/No only — raw IMEI never displayed)
- IMEI Validation at PDP & Doorstep
- QC Decision & Comments
- Pickup Partner Name
- Exchange Pickup Serviceability & Non-Serviceable Reason (conditional)

### 3. MOP & Payment – Before / After Exchange *(new section)*
Side-by-side comparison table showing pricing snapshots:
- MRP, Selling Price, Brand Discount, Payment/Card Discount
- Exchange Quote (Before) vs Actual Exchange Value (After)
- Promo Offer, Bump-Up Bonus
- Difference Explanation block (mandatory when values differ)

### 4. Refund Details *(enhanced existing section)*
- Highlighted refund calculation summary block
- Source amount + Wallet amount split cards
- Full refund field set: status, mode, dates, reference ID, UTR (role-gated), delta refund

## Business Rules Applied

| Rule | Implementation |
|---|---|
| IMEI Privacy | Only Yes/No shown — raw IMEI never rendered |
| QC Comments | Falls back to "QC Pending" when blank |
| UTR Visibility | Masked (`******1234`) for standard role |
| Non-Serviceable Reason | Shown only when pickup is not serviceable |
| Bump-Up Bonus | Displays ₹0 when not applicable |
| Difference Explanation | Always shown when before/after values differ |

## Section Order (Orders Tab)

1. Product Information *(existing)*
2. Exchange Summary *(new — auto-expanded)*
3. Order Info *(existing)*
4. MOP & Payment – Before / After Exchange *(new — auto-expanded)*
5. Delivery Details *(existing)*
6. Payment Details *(existing)*
7. Tracking List *(existing)*
8. Refund Details *(enhanced — auto-expanded when refund data present)*

## Branching Strategy

| Branch | Purpose |
|---|---|
| `main` | Stable, reviewed releases |
| `dev` | Active development — all changes go here first |

All development is done on `dev`. Changes are merged to `main` only after explicit approval.

## Source Documents

- `Kapture UI changes for Exchange Support.docx` — PRD
- `Middleware_Spec_Exchange_Main.pdf` — Middleware integration spec
- `Exchange UI & Folders .xlsx` — Field mapping and folder structure
