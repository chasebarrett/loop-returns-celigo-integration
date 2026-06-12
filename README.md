# Loop Returns @ SCARPA North America
**Implementing a Returns Platform + ERP/Commerce Integrations (Shopify ↔ Loop ↔ Celigo ↔ NetSuite)**

This repository documents the implementation of the **Loop Returns** platform at **SCARPA North America**, including the business case, legacy-state pain points, and the final operating model that connected:

- **Shopify** (commerce/refunds)
- **Loop Returns** (customer portal + returns admin)
- **Celigo (Loop–NetSuite connector)** (integration & orchestration)
- **NetSuite** (Return Authorizations, Item Receipts, Credit Memos)

> Note: This repo is written as a **portfolio case study**. It intentionally avoids proprietary configuration details (credentials, exact field mappings, internal IDs, screenshots of restricted systems).

---

## Table of Contents
- [Business Case](docs/01-business-case.md)
- [Legacy Returns Process](docs/02-legacy-process.md)
- [Solution Overview](docs/03-solution-overview.md)
- [Integration Architecture](docs/04-integration-architecture.md)
- [Project Phases](docs/05-project-phases.md)
- [Process Flows](docs/06-process-flows.md)
- [Testing & Validation](docs/07-testing-validation.md)
- [Change Management](docs/08-change-management.md)
- [Risks & Decisions](docs/09-risks-decisions.md)
- [Outcomes](docs/10-outcomes.md)
- [Lessons Learned](docs/11-lessons-learned.md)

---

## 📉 Problem
Before Loop, returns were handled via a **paper form and prepaid label placed inside each outbound order**, with heavy manual processing across teams. The process had:

- Low visibility (returns “appeared” only after a customer asked about a refund)
- Too many manual touchpoints (inspection, RA creation, item receipt, credit memo, refund batching)
- High error risk (refund timing/amount issues, record mismatches)
- Slow refund timelines and inconsistent customer experience

---

## 🎯 Goals
1. **Create end-to-end return visibility** (initiated → in transit → received → refunded → financially recorded)
2. **Reduce manual work + operational risk**
3. **Preserve operational control** at the point of physical receiving/inspection
4. Ensure refunds and financial artifacts remain **auditable** and aligned with historical accounting standards

---

## 🛠️ Solution Overview
The implementation had two primary phases:

### Phase 1 — Portal + Admin (Frontend + Operational Enablement)
- Deploy customer-facing returns portal embedded on the website
- Enable Loop Admin return management
- Achieve immediate visibility on initiated/in-transit returns (even while back-office steps remained manual)
- Replace legacy paper return authorization forms with a **printed in-box insert directing customers to the Loop Returns portal via QR code**

This ensured customers clearly understood that returns now begin online, while eliminating the need for pre-generated return labels in outbound shipments.

### Phase 2 — Integrations (Celigo Loop–NetSuite Connector)
Configure the subset of Celigo flows required to automate:
- **Loop Return → NetSuite Return Authorization**
- **NetSuite Item Receipt → Loop Process Refund**
- **Loop Refund → NetSuite Credit Memo** (accounting record)

---

## 🔑 Key Design Choice: Warehouse-Controlled Receiving
Loop’s “out-of-the-box” intended behavior can auto-create item receipts and push refunds quickly. SCARPA customized the workflow to:

- Keep **warehouse** as the source of truth for “received + inspected”
- Trigger refunds only after an **Item Receipt** is created in **NetSuite** by the warehouse team

This preserved operational control while still enabling automation + speed.

---

## 📊 Diagrams
- [Legacy process](docs/02-legacy-process.md#legacy-flow-diagram)
- [SCARPA Loop workflow](docs/06-process-flows.md#scarpa-loop-workflow-diagram)
- [Data sync architecture](docs/04-integration-architecture.md#architecture-diagram)
- [Refund → Credit Memo sequence](docs/06-process-flows.md#refund--credit-memo-sequence)

---

## 📈 Outcomes
- Replaced an opaque, paper-based returns motion with a structured lifecycle
- Reduced manual processing time and error probability
- Increased transparency for Customer Service, Warehouse, Finance, and customers
- Maintained clean, auditable records in NetSuite
- **Reduced operational load on Product Services enough that, during Spring seasonal turnover, SCARPA was able to reduce the number of seats in the department, resulting in additional cost savings**

See: [Outcomes](docs/10-outcomes.md)
