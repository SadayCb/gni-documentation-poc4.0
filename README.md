# LOAN_API — Overview

## Package Overview

`GAIA.LOAN_API` is a shared banking PL/SQL package for loan operations, financial calculations, payment schedules, accounting entries, account management, overdue processing and operation history. Its public specification exposes functions and procedures used by multiple operational flows.

The API reference documents each active public declaration separately, including overloads. Business behavior is summarized from the supplied package body; the package should not be treated as a screen-specific controller.

## Functional Areas

| Functional Area | Description | API Reference |
|---|---|---|
| Loan operations and controls | 11 public declaration(s) covering loan operations and controls. | [View methods](api.md#get-loan-amount) |
| Accounting and accounts | 11 public declaration(s) covering accounting and accounts. | [View methods](api.md#get-voucher-data-from-query) |
| Payments and allocation | 4 public declaration(s) covering payments and allocation. | [View methods](api.md#get-amount-by-range) |
| Payment schedules and dates | 26 public declaration(s) covering payment schedules and dates. | [View methods](api.md#post-int-amount-to-plan) |
| Interest, penalties and rates | 13 public declaration(s) covering interest, penalties and rates. | [View methods](api.md#get-amount-for-pen-calc-1) |
| Delinquency and status | 7 public declaration(s) covering delinquency and status. | [View methods](api.md#get-ovd-trs-oper-type) |
| Limits, tranches and overdrafts | 4 public declaration(s) covering limits, tranches and overdrafts. | [View methods](api.md#evaluate-limit-amount) |
| History, metadata and reversals | 15 public declaration(s) covering history, metadata and reversals. | [View methods](api.md#clear-addtional-data) |

## Documentation Navigation

- [API Reference](api.md)
- [Data Model](data-model.md)
- [Dependencies](dependencies.md)
- [Error Handling](error-handling.md)

## Key Technical Notes

- The specification defines reusable record/collection types and exposes overloaded public methods.
- Some operations include posting, transaction history and explicit transaction control; review their method descriptions before integration.
- Referenced external packages and database objects are identified from source usage; absent DDL prevents confirmation of physical foreign keys.
