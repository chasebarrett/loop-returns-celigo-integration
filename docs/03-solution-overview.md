# Solution Overview

## What Loop introduced
Loop added both customer-facing and operational tooling:

### Customer-facing
- A returns portal embedded on the website
- Digital initiation (no paper forms)
- Improved clarity on return steps and status

### Operational + back-office
- Loop Admin for managing return records
- Integration path enabling data sync across:
  - Shopify (refund execution)
  - Loop (return state machine / admin)
  - Celigo (integration orchestration)
  - NetSuite (RAs, item receipts, credit memos)

## The integration problem to solve
A successful system required accurate synchronization:
- **Loop → NetSuite**: create Return Authorization
- **NetSuite → Loop**: confirm receiving via Item Receipt
- **Loop → Shopify**: issue refund to customer
- **Loop → NetSuite**: create Credit Memo as financial record of the refund

## Outcome intent
Transform a manual, opaque returns workflow into one that is:
- automated where safe,
- controlled where necessary,
- and auditable end-to-end.
