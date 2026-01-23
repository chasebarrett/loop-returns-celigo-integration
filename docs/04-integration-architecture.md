# Integration Architecture

## Systems
- **Shopify**: source of order + executes customer refunds
- **Loop**: return portal + admin return record lifecycle
- **Celigo**: integration layer (Loop–NetSuite connector)
- **NetSuite**: operational + financial system of record (RAs, item receipts, credit memos)

---

## Architecture diagram

```mermaid
flowchart TB
  subgraph Customer
    C1["Customer"]
  end

  subgraph Shopify
    S1["Shopify Orders"]
    S2["Shopify Refunds"]
  end

  subgraph Loop
    L1["Loop Returns Portal"]
    L2["Loop Admin / Return Record"]
  end

  subgraph Celigo
    X1["Celigo Integration Flows (Loop-NetSuite Connector)"]
  end

  subgraph NetSuite
    N1["Return Authorization"]
    N2["Item Receipt"]
    N3["Credit Memo"]
  end

  C1 --> L1 --> L2
  S1 --> L2
  L2 --> X1 --> N1
  N2 --> X1 --> L2
  L2 --> S2
  L2 --> X1 --> N3
```
> **Note:** This diagram represents the high-level system interactions. Detailed field mappings and Celigo flow configurations were refined iteratively through testing, SME validation, and cross-functional collaboration rather than rigid upfront specifications.
