# Risks & Decisions

## Key decision: warehouse-controlled receiving
**Decision:** Keep Item Receipt creation manual (warehouse-led) rather than auto-creating receipts from Loop.

**Why:**
- Preserves operational control at physical inspection point
- Reduces risk of refunds issued before verifying condition/eligibility
- Aligns with how teams already manage receiving accountability

**Tradeoff:**
- Requires warehouse consistency and clear SOPs to avoid bottlenecks

---

## Risks (and mitigations)

### R1: Refund amount mismatches (tax, discounts, customer type)
**Mitigation:**
- Test matrix across scenarios
- SME verification for accounting + refund math

### R2: Connector/flow limitations
**Mitigation:**
- Use only flows that match the desired operating model
- Document assumptions and edge cases
- Build monitoring + exception handling habits early

### R3: Returns “stuck” between systems
**Mitigation:**
- Define “source of truth” by stage:
  - Loop = initiation/status
  - NetSuite = receiving + financial artifacts
  - Shopify = actual refund execution
- Build triage checklist (where to look first, what fields indicate progress)

### R4: Organizational friction from workflow change
**Mitigation:**
- Align early with SMEs
- Make the “why” clear (visibility, less rework, faster refunds)
- Pilot + iterate
