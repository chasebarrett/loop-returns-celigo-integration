# Project Phases

## Phase 1 — Customer Portal + Loop Admin (Enablement)
**Goal:** Move return initiation from paper to digital, immediately improving visibility.

Delivered:
- Loop returns portal embedded on the site
- Loop Admin enabled for return tracking and management

Result:
- Customers no longer received a return label in the box
- Returns began in the portal, generating real-time visibility on initiated returns

**Important:** During Phase 1, back-office artifacts (RA, item receipt, credit memo, refunds) still required manual work. Visibility improved first; automation followed in Phase 2.

---

## Phase 2 — Celigo LoopReturns–NetSuite Integration (Automation)
**Goal:** Automate the creation and synchronization of the records that make returns operationally complete and financially auditable.

Work included:
- Aligning Loop’s data model with NetSuite requirements
- Working within Celigo connector constraints
- Ensuring discounts, taxes, and customer types/refund math aligned across systems
- Testing return scenarios end-to-end with SMEs

Selected flows:
- Loop Return → NetSuite Return Authorization
- NetSuite Item Receipt → Loop Process Refund
- Loop Refund → NetSuite Credit Memo
