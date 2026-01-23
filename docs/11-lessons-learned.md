# Lessons Learned

## 1. Visibility delivers value before automation

Even before backend integrations were complete, directing customers to the Loop Returns portal immediately solved one of the largest pain points of the legacy process: lack of visibility.

Having insight into initiated and in-transit returns reduced uncertainty, customer escalations, and internal investigation time, even while some steps remained manual.

---

## 2. “Out of the box” workflows are a starting point, not a mandate

Loop’s default behavior favors speed by automatically creating Item Receipts and triggering refunds upon delivery.

SCARPA intentionally deviated from this model to maintain operational control at the physical inspection point, demonstrating that vendor-recommended workflows must often be adapted to fit real-world operational constraints.

---

## 3. Operational control should not be sacrificed for automation

Tying refund execution to warehouse-created Item Receipts ensured that:
- Refunds only occurred after physical inspection
- Accountability remained clear
- Exceptions could be handled without downstream financial cleanup

Automation was used to accelerate trusted decisions—not replace them.

---

## 4. Fewer, intentional integration flows reduce complexity

Although the LoopReturns–NetSuite connector includes approximately 15 available flows, only a subset were implemented.

This deliberate scoping:
- Reduced cognitive and operational complexity
- Made failure modes easier to reason about
- Improved long-term maintainability of the integration

---

## 5. Cross-functional iteration outperformed upfront perfection

Accurate integration behavior was achieved primarily through:
- Trial-and-error testing
- Cross-functional collaboration
- Reliance on subject matter experts to validate artifacts such as Return Authorizations and Credit Memos using test orders and test returns

This iterative approach proved more effective than attempting to design a perfect mapping model upfront.

---

## 6. Systems design can directly affect staffing requirements

By reducing manual return handling and shifting inspection responsibilities to the warehouse, the operational burden on Product Services decreased significantly.

This reduction enabled SCARPA to lower staffing levels during Spring seasonal turnover without increasing risk or backlog, illustrating that systems and workflow design decisions can have direct labor and cost implications—not just efficiency gains.
