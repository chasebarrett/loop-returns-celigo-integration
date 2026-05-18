# Process Flows

## Intended (out-of-the-box) Loop workflow
```mermaid
flowchart TD
  A[Customer initiates return] --> B[Loop return record created]
  B --> C[Celigo creates NetSuite RA]
  C --> D[Loop auto-creates Item Receipt in NetSuite]
  D --> E[Item Receipt triggers refund process]
  E --> F[Shopify refunds customer]
  F --> G[Celigo creates NetSuite Credit Memo]
```
## SCARPA workflow (customized for operational control)

> Key change: Item Receipts are not auto-created. Warehouse receives/inspects and creates the NetSuite Item Receipt.

```mermaid
flowchart TD
  A[Customer initiates return in Loop Portal] --> B[Loop return record created]
  B --> C[Celigo creates NetSuite Return Authorization]
  C --> D[Return shipped back to SCARPA]
  D --> E[Warehouse receives + inspects item]
  E --> F[Warehouse creates Item Receipt in NetSuite]
  F --> G[Item Receipt triggers Loop refund flow]
  G --> H[Shopify refunds customer]
  H --> I[Loop marks return refunded/archived]
  I --> J[Celigo creates NetSuite Credit Memo]
```
## Swimlane view (who does what)
```mermaid
flowchart LR
  subgraph Customer
    A[Initiate return in portal]
    B[Ship item back]
  end

  subgraph Loop
    C[Return record + status]
    D[Archive after refund]
  end

  subgraph Warehouse
    E[Receive + inspect]
  end

  subgraph NetSuite
    F[Return Authorization]
    G[Item Receipt]
    H[Credit Memo]
  end

  subgraph Shopify
    I[Refund transaction]
  end

  A --> C
  C --> F
  B --> E
  E --> G
  G --> I
  I --> D
  D --> H
```
## Refund → Credit Memo sequence (timing + dependencies)
```mermaid
sequenceDiagram
  participant W as Warehouse
  participant NS as NetSuite
  participant C as Celigo
  participant L as Loop
  participant S as Shopify

  W->>NS: Create Item Receipt (after receiving/inspection)
  NS->>C: Item Receipt available for export
  C->>L: Trigger "Process Refund" update
  L->>S: Initiate refund transaction
  S-->>L: Refund confirmed
  L-->>L: Mark return refunded/archived
  L->>C: Return status/refund data available
  C->>NS: Create Credit Memo (financial record)
```
