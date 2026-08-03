# Field-Level Source Control Rules

Apply these rules at the field level. A lower-authority source may remain valid for unrelated fields.

1. `revision_history.csv`
   - An `approved` revision controls only the field named in `revised_field`.
   - A `superseded` revision is rejected.
   - Unrelated values remain controlled by their ordinary sources.

2. `purchase_order_register.csv`
   - Controls `po_id`, `supplier_id`, supplier identity, supplier tier, SKU, ordered quantity,
     unit cost, original required date, and receiving site.

3. `supplier_acknowledgements.csv`
   - An accepted acknowledgement controls acknowledged quantity and promised delivery date,
     unless an approved field-specific revision replaces that exact field.

4. `shipment_event_log.csv`
   - A structurally valid delivered event controls actual delivery timestamp and date.
   - For a malformed row, preserve fields whose positions and meanings remain uniquely
     determinable. Limit uncertainty to the ambiguous fields.
   - Do not convert non-decision-critical uncertainty into a case-level verification hold.

5. `warehouse_receipt_log.csv`
   - A posted receipt controls received quantity and receipt timestamp.

6. `quality_inspection_log.csv`
   - Controls rejected quantity, disposition, and quality-hold status.

7. `supplier_contract_terms.csv`
   - Controls shortage rate, damage rate, and debit cap by supplier tier.

8. `inventory_adjustment_ledger.csv`
   - Controls posted supplier-debit amount when the row is valid or reconstructable.
   - An extra unquoted comma confined to the final notes field is reconstructable by joining
     the trailing fragments into one notes value.

9. `expedite_authorizations.csv`
   - Controls authorized expedite amount.

10. `freight_invoice_ledger.csv`
    - Controls invoiced expedite amount.

11. `supplier_scorecard.csv`
    - Controls the source supplier-qualification value.
    - Values outside the allowed vocabulary in `service_level_rules.json` become
      `supplier_qualification_status=Needs verification`.

12. `duplicate_case_register.csv`
    - Controls duplicate-only status. Duplicate-only records are excluded from active-case
      outputs but retained in the shipment exception report and rejection register.
