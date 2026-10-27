# LOAN_API — Data Model

[Back to Overview](README.md) · [API Reference](api.md)

## Database Objects

The objects below are identified from SQL statements in the supplied package body. Operations are syntactically extracted; `READ` denotes query use. They are not a database catalog or DDL-backed inventory.

| Database Object | Type | Operation | Used By |
|---|---|---|---|
| `CARDS_ALL` | Referenced database object | READ, UPDATE | [evaluate-limit-amount](api.md#evaluate-limit-amount), [create-overdrafts](api.md#create-overdrafts) |
| `CREATE_SCHEDULE_PARAMETRS` | Referenced database object | READ | [get-created-schedule](api.md#get-created-schedule) |
| `CS_ACCOUNT` | Referenced database object | READ, UPDATE | [evaluate-limit-amount](api.md#evaluate-limit-amount), [get-loan-amount](api.md#get-loan-amount), [get-gl-acc-from-matrix](api.md#get-gl-acc-from-matrix) (+16) |
| `EOD_PROGRAMS_EXCEPTION` | Referenced database object | READ | [do-auto-payment](api.md#do-auto-payment), [do-int-calculation](api.md#do-int-calculation), [create-overdrafts](api.md#create-overdrafts) |
| `GAIA.CS_ACCOUNT` | Referenced database object | READ | [get-ovd-date](api.md#get-ovd-date) |
| `GAIA.KRD_TEKLIF_DETAY` | Referenced database object | READ, UPDATE | [update-payment-plan](api.md#update-payment-plan) |
| `GAIA.KRD_TESIS` | Referenced database object | UPDATE | [update-payment-plan](api.md#update-payment-plan) |
| `GAIA.LOAN_CATEGORY` | Referenced database object | READ | [evaluate-limit-amount](api.md#evaluate-limit-amount) |
| `GAIA.LOAN_OPERATION_HISTORY` | Referenced database object | READ | [evaluate-limit-amount](api.md#evaluate-limit-amount) |
| `GAIA.LOAN_PAYMENT_PLAN` | Referenced database object | READ | [get-ovd-trs-oper-type](api.md#get-ovd-trs-oper-type) |
| `GLBL_TRANSACTION` | Referenced database object | READ, UPDATE | [do-create-tranche](api.md#do-create-tranche), [do-delete-operation](api.md#do-delete-operation), [create-loan-history](api.md#create-loan-history) |
| `GL_ACCOUNT_DEFINE` | Referenced database object | READ | [get-gl-acc-active-passive](api.md#get-gl-acc-active-passive) |
| `GL_JOURNAL_LINES` | Referenced database object | READ | [do-delete-operation](api.md#do-delete-operation), [create-loan-history](api.md#create-loan-history), [update-loan-history](api.md#update-loan-history) |
| `GL_URUN_HESAP_PR` | Referenced database object | READ | [get-gl-acc-from-matrix](api.md#get-gl-acc-from-matrix) |
| `IBS.ONLINE_CRD_BLOCK` | Referenced database object | READ, UPDATE | [update-payment-plan](api.md#update-payment-plan) |
| `KRD_FON_VERILME` | Referenced database object | UPDATE | [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out) |
| `KRD_GUARANTEE_MAIN` | Referenced database object | READ | [get-amount-for-pen-calc-1](api.md#get-amount-for-pen-calc-1) |
| `KRD_KOM_EOD` | Referenced database object | INSERT, READ, UPDATE | [do-commission-recognition](api.md#do-commission-recognition) |
| `KRD_KOM_PLAN_DETAY` | Referenced database object | DELETE, INSERT, READ, UPDATE | [table-log-operation](api.md#table-log-operation), [do-commission-recognition](api.md#do-commission-recognition), [do-com-schedule-allignment](api.md#do-com-schedule-allignment) |
| `KRD_KOM_PLAN_DETAY_LOG` | Referenced database object | DELETE, INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `KRD_ODEME_PLAN` | Referenced database object | READ | [init-global-variables](api.md#init-global-variables) |
| `KRD_SCOR_AUTO_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_EMANET_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_ESYA_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_MAIN` | Referenced database object | READ | [is-online-offer](api.md#is-online-offer) |
| `KRD_SCOR_ODEME_PLAN` | Referenced database object | READ | [get-schedule-from-memo](api.md#get-schedule-from-memo) |
| `KRD_SCOR_QARANT_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_REAL_ESTATE_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_SEHMLER_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_TEMINAT_ALAKA_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SCOR_ZAMIN_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_SKOR_GIROV_OTHER_C` | Referenced database object | READ, UPDATE | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_TEKLIF` | Referenced database object | READ | [init-global-variables](api.md#init-global-variables) |
| `KRD_TEKLIF_DETAY` | Referenced database object | READ, UPDATE | [evaluate-limit-amount](api.md#evaluate-limit-amount), [reverse-update](api.md#reverse-update), [do-create-tranche](api.md#do-create-tranche) (+16) |
| `KRD_TEKLIF_NO` | Referenced database object | INSERT, UPDATE | [get-offer-id](api.md#get-offer-id) |
| `KRD_TEMINAT_TIP_PR` | Referenced database object | READ | [do-loan-collateral-out](api.md#do-loan-collateral-out) |
| `KRD_TESIS` | Referenced database object | READ, UPDATE | [create-account](api.md#create-account), [do-commission-recognition](api.md#do-commission-recognition), [do-guarantee-out](api.md#do-guarantee-out) (+4) |
| `LOAN_ACCOUNTS` | Referenced database object | READ | [create-account](api.md#create-account) |
| `LOAN_ACC_TYPES_PR` | Referenced database object | READ | [post-int-amount-to-plan](api.md#post-int-amount-to-plan), [get-amount-for-pen-calc-1](api.md#get-amount-for-pen-calc-1), [create-account](api.md#create-account) (+1) |
| `LOAN_ACC_TYPE_MAPPING` | Referenced database object | READ | [get-acc-type-by-status](api.md#get-acc-type-by-status) |
| `LOAN_AMOUNT_RANGE_INFO` | Referenced database object | READ | [get-amount-by-range](api.md#get-amount-by-range) |
| `LOAN_CATEGORY` | Referenced database object | DELETE, INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `LOAN_CATEGORY_TEMP` | Referenced database object | DELETE, INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `LOAN_EOD_AUTO_CLOSE` | Referenced database object | INSERT, READ | [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out) |
| `LOAN_EOD_CONTROL` | Referenced database object | INSERT, READ | [do-loan-control-1](api.md#do-loan-control-1), [do-loan-control-2](api.md#do-loan-control-2) |
| `LOAN_EOD_CONTROL_EXP` | Referenced database object | READ | [do-plan-control](api.md#do-plan-control), [do-loan-control-2](api.md#do-loan-control-2) |
| `LOAN_FLOW_RATIO_INFO` | Referenced database object | DELETE, INSERT, READ | [table-log-operation](api.md#table-log-operation), [do-int-calculation](api.md#do-int-calculation), [get-flow-ratio-info](api.md#get-flow-ratio-info) |
| `LOAN_FLOW_RATIO_INFO_LOG` | Referenced database object | INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `LOAN_GLOBAL_PARAMETERS_PR` | Referenced database object | READ | [get-gl-value](api.md#get-gl-value) |
| `LOAN_HISTORY_MAPPING` | Referenced database object | READ | [add-column-update-1](api.md#add-column-update-1) |
| `LOAN_INT_CALCULATION_DIFF_HISTORY` | Referenced database object | DELETE, INSERT, READ, UPDATE | [loan-int-diff-operation](api.md#loan-int-diff-operation) |
| `LOAN_INT_CALC_STOP_FOR_GRACE` | Referenced database object | READ | [do-int-calculation](api.md#do-int-calculation) |
| `LOAN_INT_CALC_TYPES_PR` | Referenced database object | READ | [get-interest-calc-info](api.md#get-interest-calc-info), [get-basis-year-days-cnt](api.md#get-basis-year-days-cnt) |
| `LOAN_OPERATION_DESC` | Referenced database object | READ | [get-trn-caller-id](api.md#get-trn-caller-id), [create-journal-entries](api.md#create-journal-entries), [create-loan-history](api.md#create-loan-history) (+1) |
| `LOAN_OPERATION_HISTORY` | Referenced database object | INSERT, MERGE, READ, UPDATE | [get-additional-info](api.md#get-additional-info), [reverse-update](api.md#reverse-update), [do-delete-operation](api.md#do-delete-operation) (+3) |
| `LOAN_OPERATION_VOUCHER` | Referenced database object | READ | [create-journal-entries](api.md#create-journal-entries) |
| `LOAN_OVERDUE_MAPPING` | Referenced database object | READ | [do-overdue-transit-operation](api.md#do-overdue-transit-operation) |
| `LOAN_OVERDUE_TRANSIT_QUEUE` | Referenced database object | READ | [do-overdue-transit-operation](api.md#do-overdue-transit-operation) |
| `LOAN_PAYMENT_PLAN` | Referenced database object | DELETE, INSERT, READ, UPDATE | [post-int-amount-to-plan](api.md#post-int-amount-to-plan), [get-amount-for-pen-calc-1](api.md#get-amount-for-pen-calc-1), [get-ovd-trs-oper-type](api.md#get-ovd-trs-oper-type) (+16) |
| `LOAN_PAYMENT_PLAN_LOG` | Referenced database object | INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `LOAN_PORTFOLIO_LITE` | Referenced database object | READ | [do-loan-status-control](api.md#do-loan-status-control), [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out) |
| `LOAN_SPECIAL_DAYS_PR` | Referenced database object | READ | [get-amount-for-pen-calc-2](api.md#get-amount-for-pen-calc-2) |
| `LOAN_STOP_RATIO_INFO` | Referenced database object | DELETE, INSERT, READ | [table-log-operation](api.md#table-log-operation), [do-int-calculation](api.md#do-int-calculation), [get-stop-ratio-info](api.md#get-stop-ratio-info) |
| `LOAN_STOP_RATIO_INFO_LOG` | Referenced database object | INSERT, READ | [table-log-operation](api.md#table-log-operation) |
| `LOAN_TEMPORARY_PAYMENT_PLAN` | Referenced database object | INSERT, READ | [update-payment-plan](api.md#update-payment-plan) |
| `LOAN_TRANCHE_INFO` | Referenced database object | READ | [add-column-update-1](api.md#add-column-update-1) |
| `LOAN_TRANCHE_LIMIT_CHANGES_HISTORY` | Referenced database object | READ | [do-loan-close-with-collateral-out](api.md#do-loan-close-with-collateral-out) |
| `LOAN_TRANCHE_PAYMENT_PLAN` | Referenced database object | READ, UPDATE | [post-int-amount-to-plan](api.md#post-int-amount-to-plan) |
| `ODEME_PLAN_TMP` | Referenced database object | READ | [update-payment-plan](api.md#update-payment-plan) |
| `ODEME_PLAN_TMP2` | Referenced database object | READ, UPDATE | [get-special-schedule](api.md#get-special-schedule) |
| `PKRD_TURKOD_PR` | Referenced database object | READ | [get-overdue-min-amount](api.md#get-overdue-min-amount), [get-overdue-grace-days](api.md#get-overdue-grace-days) |
| `SP_FAIZ_GUN_TANIM_PR` | Referenced database object | READ | [create-account](api.md#create-account) |
| `SP_URUN_PR` | Referenced database object | READ | [get-gl-acc-from-matrix](api.md#get-gl-acc-from-matrix) |
| `SS_MUH1201_0_LOG` | Referenced database object | READ | [do-journal-entry](api.md#do-journal-entry), [create-journal-entries](api.md#create-journal-entries) |
| `TEMP_CARD_BALANCE` | Referenced database object | INSERT | [create-overdrafts](api.md#create-overdrafts) |

## Important Data Relationships

The supplied files do not include database DDL or foreign-key definitions. Relationships observed through joins or loan document identifiers are application-level references and must not be treated as confirmed foreign-key constraints.

## Data Modification Notes

Loan-account, payment-plan, limit, journal, history and status modifications are documented under the related [API methods](api.md#api-index). Review transaction effects for posting and EOD/SOD operations.
