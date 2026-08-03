# Supply Chain Exception Reconciliation Benchmark

**Repository name:** `supply-chain-exception-reconciliation-benchmark`

**Description:** A source-grounded benchmark for evaluating supply chain managers on purchase-order, receipt, OTIF, freight-cost, supplier-risk, and malformed-record reconciliation.

This repository contains a synthetic supply-chain exception packet and a benchmark prompt.
The task tests whether a model can reconcile purchase orders, supplier acknowledgements,
shipment events, warehouse receipts, quality inspections, supplier debit postings,
expedite costs, approved revisions, supplier qualification evidence, malformed source rows,
and duplicate cases.

## Benchmark objective

The benchmark is designed to produce reasoning-based differentiation rather than a simple
formatting failure. The most difficult decisions require the model to:

- apply a field-level source hierarchy;
- restrict an approved revision to the field it actually changes;
- distinguish a fully reconstructable malformed row from a partially reconstructable row;
- preserve reliable fields when uncertainty is limited to non-decision-critical fields;
- calculate OTIF, quantity variances, supplier-debit eligibility, and financial reconciliation;
- propagate decision-critical uncertainty without over-propagating unrelated uncertainty;
- exclude a duplicate-only case from active-case outputs while retaining duplicate evidence.

## Required model outputs

The benchmark prompt requires six `.xlsx` workbooks. Evaluation must inspect the generated
workbooks directly. Narrative response text, code, and tool logs are not substitutes for
the required artifacts.

## Files

- `BENCHMARK_PROMPT.md` — complete task and output specification
- `case_intake_register.csv`
- `purchase_order_register.csv`
- `supplier_acknowledgements.csv`
- `revision_history.csv`
- `shipment_event_log.csv`
- `warehouse_receipt_log.csv`
- `quality_inspection_log.csv`
- `supplier_contract_terms.csv`
- `inventory_adjustment_ledger.csv`
- `expedite_authorizations.csv`
- `freight_invoice_ledger.csv`
- `supplier_scorecard.csv`
- `duplicate_case_register.csv`
- `service_level_rules.json`
- `source_schema_manifest.json`
- `source_control_rules.md`
- `LICENSE`

## License

The synthetic benchmark materials are dedicated to the public domain under CC0 1.0 Universal.
