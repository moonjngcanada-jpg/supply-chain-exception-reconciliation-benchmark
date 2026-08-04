# Supply Chain Exception Reconciliation Benchmark

A source-grounded benchmark for purchase-order, receipt, OTIF, supplier-debit, expedite-cost, supplier-risk, revision, source-integrity, and duplicate-case reconciliation.

The benchmark uses the existing file set. Its central reasoning test is parser-safe: the adjustment ledger contains a duplicate-key conflict with different posted amounts. A correct solution must avoid summing or selecting one conflicting row and must propagate decision-critical uncertainty. A separate malformed shipment row tests whether non-critical uncertainty is correctly contained.

Evaluate the six submitted `.xlsx` workbooks directly, not the model’s narrative response.

License: CC0 1.0 Universal.
