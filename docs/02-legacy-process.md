# Legacy Returns Process (Pre-Loop)

## How it worked
1. Customer received a printed return authorization form + prepaid label in the box
2. Customer filled out the form and shipped the item back
3. Product Services inspected the item manually
4. Product Services manually created in NetSuite:
   - Return Authorization (RA)
   - Item Receipt
   - Credit Memo
5. Customer Service batched and processed refunds manually

## Key issues
- **No visibility**: returns often surfaced only when a customer followed up
- **Excess manual touchpoints**: multiple teams, multiple artifacts
- **High risk of errors**: incorrect amounts, delayed refunds, record inconsistencies
- **Poor customer experience**: long or inconsistent refund timelines

---

## Legacy flow diagram

```mermaid
flowchart TD
  A[Customer receives order<br/>with prepaid return-label] --> B[Customer decides to return product, uses prepaid -return-label to ship product]
  B --> C[Return arrives at SCARPA]
  C --> D[Product Services inspects item]
  D --> E[Create Return Authorization in NetSuite]
  E --> F[Create Item Receipt in NetSuite]
  F --> G[Create Credit Memo in NetSuite]
  G --> H[Customer Service batches refunds<br/>and processes refunds manually]
  H --> I[Customer receives refund]
