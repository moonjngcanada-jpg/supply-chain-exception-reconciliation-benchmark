# Field-Level Source Control Rules

Resolve authority by field, not by whole file.

1. Approved revisions control only `revised_field`; superseded revisions are rejected.
2. The PO register controls supplier, tier, SKU, ordered quantity, cost, required date, and site.
3. Accepted acknowledgements control acknowledged quantity and promised date unless that exact field has an approved revision.
4. Delivered shipment events control actual delivery time. For malformed rows, retain only fields whose positions and meanings remain unique.
5. Posted receipts control received quantity; quality inspections control rejected quantity, disposition, and hold status.
6. Contract terms control debit rates and caps.
7. The adjustment ledger controls posted supplier debit only when `amount_usd` is uniquely determinable from a valid or reconstructable row.
8. Expedite authorizations control authorized cost; freight invoices control invoiced cost.
9. Supplier scorecards control the source qualification value. Values outside the allowed vocabulary become `Needs verification`.
10. Duplicate-register records are excluded from active-case outputs and retained in exception and rejection evidence.

A malformed row can contain both reliable and uncertain fields. Limit uncertainty to ambiguous fields. Propagate `Needs verification` only when an ambiguous field is decision-critical.
