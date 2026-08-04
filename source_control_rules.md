# Field-Level Source Control Rules

Resolve authority by field, not by whole file.

1. `case_intake_register.csv` controls issue type, requested remediation, requested expedite amount, opening time, and intake priority.
2. `purchase_order_register.csv` controls PO, supplier, tier, SKU, ordered quantity, cost, required date, and receiving site.
3. An accepted `supplier_acknowledgements.csv` record controls acknowledged quantity and promised date unless an approved revision replaces that exact field.
4. An approved `revision_history.csv` row controls only `revised_field`; a superseded revision is rejected.
5. `shipment_event_log.csv` controls actual delivery time. For a malformed row, retain fields whose positions and meanings remain unique and limit uncertainty to the ambiguous fields.
6. `warehouse_receipt_log.csv` controls received quantity. `quality_inspection_log.csv` controls rejected quantity, disposition, and quality hold.
7. `supplier_contract_terms.csv` controls debit rates and caps.
8. `inventory_adjustment_ledger.csv` controls posted supplier debit only when the applicable posting is uniquely established.
   - Before aggregation, check duplicate `adjustment_id` values.
   - If the same `adjustment_id` appears more than once with different `amount_usd` values and no row is explicitly marked as a reversal, void, or correction, the posted amount is `Needs verification`.
   - Do not sum the conflicting rows and do not select one by row order or timestamp.
9. `expedite_authorizations.csv` controls authorized expedite cost; `freight_invoice_ledger.csv` controls invoiced expedite cost.
10. `supplier_scorecard.csv` controls the source qualification value. Values outside the allowed vocabulary become `Needs verification`.
11. `duplicate_case_register.csv` controls duplicate-only status. Duplicate-only records are excluded from active-case outputs and retained in exception and rejection evidence.

A source anomaly may affect only part of a record. Propagate `Needs verification` only through fields that depend on a decision-critical uncertain value.
