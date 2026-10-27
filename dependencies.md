# LOAN_API — Dependencies

[Back to Overview](README.md) · [API Reference](api.md)

## Referenced Packages and Interfaces

Direct dotted calls identified in the supplied package body; some references may denote SQL objects or object methods where source declarations are unavailable.

| Dependency | Type | Used By |
|---|---|---|
| `GLBL_FAIZ` | Referenced PL/SQL qualifier | [do-int-calculation](api.md#do-int-calculation), [get-amount-for-pen-calc-2](api.md#get-amount-for-pen-calc-2), [get-annuity-schedule](api.md#get-annuity-schedule), [get-commission-schedule](api.md#get-commission-schedule), [get-plan-month-count](api.md#get-plan-month-count) (+4) |
| `LOAN_TRANCHE_API` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-create-tranche](api.md#do-create-tranche), [do-delete-operation](api.md#do-delete-operation), [finalize-addtional-process](api.md#finalize-addtional-process), [get-ovd-date](api.md#get-ovd-date) (+4) |
| `GLBL_TARIH` | Referenced PL/SQL qualifier | [create-account](api.md#create-account), [do-commission-recognition](api.md#do-commission-recognition), [do-int-calculation](api.md#do-int-calculation), [get-commission-schedule](api.md#get-commission-schedule), [get-interest-calc-dates](api.md#get-interest-calc-dates) (+3) |
| `TRN_BROKER` | Referenced PL/SQL qualifier | [create-loan-history](api.md#create-loan-history), [do-guarantee-out](api.md#do-guarantee-out), [do-journal-entry](api.md#do-journal-entry), [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out), [do-loan-collateral-out](api.md#do-loan-collateral-out) (+2) |
| `GLBL_HESAP` | Referenced PL/SQL qualifier | [change-account-status](api.md#change-account-status), [create-overdrafts](api.md#create-overdrafts), [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out), [evaluate-limit-amount](api.md#evaluate-limit-amount), [get-gl-acc-from-matrix](api.md#get-gl-acc-from-matrix) (+1) |
| `GNI_MESSAGE` | Referenced PL/SQL qualifier | [create-account](api.md#create-account), [do-loan-status-control](api.md#do-loan-status-control), [get-commission-schedule](api.md#get-commission-schedule), [get-new-acc](api.md#get-new-acc), [get-pym-startdate](api.md#get-pym-startdate) |
| `RUHA3H` | Referenced PL/SQL qualifier | [add-additional-group](api.md#add-additional-group), [add-additional-info-1](api.md#add-additional-info-1), [add-column-update-1](api.md#add-column-update-1), [clear-addtional-data](api.md#clear-addtional-data), [end-additional-group](api.md#end-additional-group) |
| `GLBL_BAKIYE` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-commission-recognition](api.md#do-commission-recognition), [do-guarantee-out](api.md#do-guarantee-out), [do-non-cash-loan-close](api.md#do-non-cash-loan-close) |
| `GNI_UTILITY` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-int-calculation](api.md#do-int-calculation), [do-loan-control-1](api.md#do-loan-control-1), [do-overdue-transit-operation](api.md#do-overdue-transit-operation) |
| `APEX_JSON` | Referenced PL/SQL qualifier | [add-additional-group](api.md#add-additional-group), [add-additional-info-1](api.md#add-additional-info-1), [get-created-schedule](api.md#get-created-schedule) |
| `GLBL` | Referenced PL/SQL qualifier | [do-loan-control-2](api.md#do-loan-control-2), [get-plan-error](api.md#get-plan-error), [loan-int-diff-operation](api.md#loan-int-diff-operation) |
| `LOAN_REPORT_API` | Referenced PL/SQL qualifier | [do-int-calculation](api.md#do-int-calculation), [do-overdue-transit-operation](api.md#do-overdue-transit-operation), [evaluate-limit-amount](api.md#evaluate-limit-amount) |
| `MM_ACCOUNTING#` | Referenced PL/SQL qualifier | [do-delete-operation](api.md#do-delete-operation), [do-journal-entry](api.md#do-journal-entry), [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `APEX_KRD2204_0_API_P` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-create-tranche](api.md#do-create-tranche) |
| `APEX_KRD2220_0_API_P` | Referenced PL/SQL qualifier | [do-guarantee-out](api.md#do-guarantee-out), [do-non-cash-loan-close](api.md#do-non-cash-loan-close) |
| `GLBL_CCY` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `GLBL_EOD` | Referenced PL/SQL qualifier | [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out), [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `JSON_OBJECT_T` | Referenced PL/SQL qualifier | [get-additional-info](api.md#get-additional-info), [reverse-update](api.md#reverse-update) |
| `KRD2204_0_API` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment), [do-create-tranche](api.md#do-create-tranche) |
| `KRD2220_0_API` | Referenced PL/SQL qualifier | [do-guarantee-out](api.md#do-guarantee-out), [do-non-cash-loan-close](api.md#do-non-cash-loan-close) |
| `KRD_EOD` | Referenced PL/SQL qualifier | [do-commission-recognition](api.md#do-commission-recognition), [do-delete-operation](api.md#do-delete-operation) |
| `L_OBJ` | Referenced PL/SQL qualifier | [get-additional-info](api.md#get-additional-info), [reverse-update](api.md#reverse-update) |
| `PA_API#` | Referenced PL/SQL qualifier | [do-journal-entry](api.md#do-journal-entry), [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `APEX_KRD2204_2_API_P` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment) |
| `APEX_KRD2204_7_API_P` | Referenced PL/SQL qualifier | [do-auto-payment](api.md#do-auto-payment) |
| `API_CALENDAR` | Referenced PL/SQL qualifier | [update-payment-plan](api.md#update-payment-plan) |
| `API_VISTA` | Referenced PL/SQL qualifier | [create-overdrafts](api.md#create-overdrafts) |
| `BLOKE_API` | Referenced PL/SQL qualifier | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `DBMS_SQL` | Referenced PL/SQL qualifier | [get-voucher-data-from-query](api.md#get-voucher-data-from-query) |
| `GLBL_NAME` | Referenced PL/SQL qualifier | [create-account](api.md#create-account) |
| `GLOG` | Referenced PL/SQL qualifier | [do-com-schedule-allignment](api.md#do-com-schedule-allignment) |
| `LOAN_CATEGORY_API` | Referenced PL/SQL qualifier | [change-account-status](api.md#change-account-status) |
| `L_LOG` | Referenced PL/SQL qualifier | [reverse-update](api.md#reverse-update) |
| `L_OLD` | Referenced PL/SQL qualifier | [reverse-update](api.md#reverse-update) |
| `L_TRN` | Referenced PL/SQL qualifier | [reverse-update](api.md#reverse-update) |
| `L_TRNS` | Referenced PL/SQL qualifier | [reverse-update](api.md#reverse-update) |
| `PH_API` | Referenced PL/SQL qualifier | [do-loan-collateral-out](api.md#do-loan-collateral-out) |

## Integration Notes

- `GLBL` and loan-related packages are called directly where shown; their internal behavior cannot be verified from these two source files.
- Database object usage is catalogued separately in the [Data Model](data-model.md).
- External-service contracts, database links and configuration semantics are not asserted unless directly evidenced by the provided code.
