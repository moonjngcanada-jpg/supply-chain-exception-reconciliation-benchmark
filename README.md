# Supply Chain Exception Reconciliation Benchmark

A source-grounded benchmark for purchase-order, receipt, OTIF, supplier-debit, expedite-cost, supplier-risk, malformed-row, revision, and duplicate-case reconciliation.

## Design
The prompt is intentionally short. Exact output schemas are stored in `output_schema_manifest.json`, source schemas in `source_schema_manifest.json`, and decision logic in the rules files.

The central reasoning test is field-scoped uncertainty:
- one malformed shipment row preserves a reliable delivery timestamp while leaving only trailing evidence fields uncertain;
- one malformed adjustment row leaves the posted supplier-debit amount ambiguous, so the uncertainty must propagate through financial reconciliation and final status.

This distinction is intended to produce reasoning-based model separation rather than a formatting-only failure.

## Evaluation
Evaluate the six submitted `.xlsx` workbooks directly. Do not run rubrics against narrative model text.

## License
CC0 1.0 Universal.
