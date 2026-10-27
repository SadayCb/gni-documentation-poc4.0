# LOAN_API — Error Handling

[Back to Overview](README.md) · [API Reference](api.md)

## Verified Application Messages

The table lists distinctive literal messages passed to application error routines, where identifiable from source. Fragments containing concatenated values are displayed as literal prefixes rather than reconstructed messages. Generic exception blocks are excluded.

| API Method | Error / Condition | Meaning / Behavior |
|---|---|---|
| [post_int_amount_to_plan](api.md#post-int-amount-to-plan) | `Account type{` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_auto_payment](api.md#do-auto-payment) | `Auto payment type should be 1-Plan payment or 2-Off plan payment!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_account](api.md#create-account) | `Balance account for` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [add_payment_details](api.md#add-payment-details) | `Can not find Acc_type : {` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_acc_type_by_status](api.md#get-acc-type-by-status) | `Can not find acc type [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [update_loan_history](api.md#update-loan-history) | `Can not find information in [loan_operation_history] with tx fid [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [reverse_update](api.md#reverse-update), [do_delete_operation](api.md#do-delete-operation) | `Can not get additional info in [loan_operation_history] with tx fid [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [reverse_update](api.md#reverse-update) | `Can not get find loan[` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_create_tranche](api.md#do-create-tranche) | `Does not find loan in [krd_teklif_detay] with contract_no [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_active_passive](api.md#get-gl-acc-active-passive) | `Encountered error in gl_account_define                               table in search of account_no:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_value](api.md#get-gl-value) | `Encountered error in search of parameter {` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_active_passive](api.md#get-gl-acc-active-passive) | `Encountered more than one row in gl_account_define                               table in search of account_no:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [update_loan_history](api.md#update-loan-history) | `Find duplicate information in [loan_operation_history] with tx fid [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_voucher_data_from_query](api.md#get-voucher-data-from-query) | `GROUP_CODE field is not defined in query or GROUP_CODE field is null!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_loan_delay_int_rate_upd](api.md#do-loan-delay-int-rate-upd) | `Gecikme Faizi 0-dan ferqli oldugu halda son gecikme faizi 0-dir!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_create_tranche](api.md#do-create-tranche) | `In Creation this parameteres cant be p_contract_no or p_tranche_amount null!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_int_calculation](api.md#do-int-calculation) | `Int calculation has not finished yet for loans without transit process!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_interest_calc_dates](api.md#get-interest-calc-dates), [get_interest_calc_dates_ex](api.md#get-interest-calc-dates-ex) | `Interest calculation should be done at EOD or SOD!!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_non_cash_loan_close](api.md#do-non-cash-loan-close), [do_loan_delay_int_rate_upd](api.md#do-loan-delay-int-rate-upd) | `Kreditde sehv:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [change_account_status](api.md#change-account-status) | `Loan Status Has More Than 1 Value !` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [change_account_status](api.md#change-account-status) | `Loan Status Not Found!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_overdue_transit_operation](api.md#do-overdue-transit-operation) | `Loan product code not found in pkrd_turkod_pr table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [change_account_status](api.md#change-account-status) | `Loan with doc_no:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_from_matrix](api.md#get-gl-acc-from-matrix) | `Many rows found in gl_urun_hesap_pr table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_new_ov_cont_no](api.md#get-new-ov-cont-no) | `Musteri hesabi tapilmadi!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_new_ov_cont_no](api.md#get-new-ov-cont-no) | `Musteri melumatlarinda sehv var!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_from_matrix](api.md#get-gl-acc-from-matrix) | `No data found in gl_urun_hesap_pr table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_by_range](api.md#get-amount-by-range) | `No data found in loan_amount_range_info table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_journal_entries](api.md#create-journal-entries) | `No data found in loan_operation_desc!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_account](api.md#create-account) | `No data found in table loan_acc_types_pr with params p_acc_type:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_created_schedule](api.md#get-created-schedule) | `No record found for fid =` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_delete_operation](api.md#do-delete-operation) | `Not declared delete operation [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_int_calculation](api.md#do-int-calculation) | `Not working day may be 1 or 2, please check 22401 app,                                        for product code:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [change_account_status](api.md#change-account-status) | `Only followings p_status are accepted O-open, C-close!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [table_log_operation](api.md#table-log-operation) | `Oper type should be LOGGING-for logging or RESTORING-for restoring` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_trn_caller_id](api.md#get-trn-caller-id) | `Operation type` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [loan_int_diff_operation](api.md#loan-int-diff-operation) | `Operation type must be INS, OPEN, CLOSE!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_ovd_trs_oper_type](api.md#get-ovd-trs-oper-type) | `Overdue amount {` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_for_pen_calc](api.md#get-amount-for-pen-calc-1) | `Overdue int in plan or ovd_balance amount for penalty calculation is negative!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_interest_calc_dates](api.md#get-interest-calc-dates), [get_interest_calc_dates_ex](api.md#get-interest-calc-dates-ex) | `P_EOD_SOD param should be E - EOD or S - SOD!!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [generate_allocated_payment_list](api.md#generate-allocated-payment-list) | `Payment amount cant be more than balance amount!                             Please check amount of acc_type:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [generate_allocated_payment_list](api.md#generate-allocated-payment-list) | `Payment amount cant be negative!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [generate_allocated_payment_list](api.md#generate-allocated-payment-list), [add_payment_details](api.md#add-payment-details) | `Payment branch or customer or account is null Pymt_branch_no:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_interest_calc_info](api.md#get-interest-calc-info) | `Payment day cant be null, please check!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [post_int_amount_to_plan](api.md#post-int-amount-to-plan) | `Plan with acc_type {` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [post_int_amount_to_plan](api.md#post-int-amount-to-plan) | `Posting amounts is not allowed for this account type{` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_overdue_min_amount](api.md#get-overdue-min-amount), [get_overdue_grace_days](api.md#get-overdue-grace-days) | `Product code` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_int_calculation](api.md#do-int-calculation) | `Product code not found in pkrd_turkod_pr table,                    pls check 22401 app for this loan product!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_journal_entries](api.md#create-journal-entries) | `Query column:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_voucher_data_from_query](api.md#get-voucher-data-from-query) | `Result of query is empty!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_acc_type_by_status](api.md#get-acc-type-by-status) | `Something went wrong in [loan_acc_type_mapping], Acc Type [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [table_log_operation](api.md#table-log-operation) | `Table name should be [LOAN_PAYMENT_PLAN],[LOAN_FLOW_RATIO_INFO],[LOAN_STOP_RATIO_INFO],[LOAN_CATEGORY],[KRD_KOM_PLAN_DETAY]` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_commission_recognition](api.md#do-commission-recognition) | `This Program can run only last day of month!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [update_payment_plan](api.md#update-payment-plan) | `This operation cannot be initialized when [with_tranche_info_yn] = ''Y''` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_by_range](api.md#get-amount-by-range) | `Too many rows found in loan_amount_range_info table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_journal_entries](api.md#create-journal-entries) | `Too many rows found in loan_operation_desc!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_for_pen_calc](api.md#get-amount-for-pen-calc-2) | `Too many rows in loan_special_days_pr for date:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_value](api.md#get-gl-value) | `Too many rows in search of parameter{` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_interest_calc_info](api.md#get-interest-calc-info) | `Transaction date cant be less than last calculation date!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_loan_history](api.md#create-loan-history) | `Transaction with tx_fid:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [update_payment_plan](api.md#update-payment-plan) | `Update payment plan block ->` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_journal_entries](api.md#create-journal-entries) | `Voucher for the group_code:` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_loan_history](api.md#create-loan-history) | `You need delete this operation(s) [` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [init_global_variables](api.md#init-global-variables) | `[krd_odeme_plan] is invalid` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [init_global_variables](api.md#init-global-variables) | `[krd_teklif] is invalid` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [init_global_variables](api.md#init-global-variables) | `[krd_teklif_detay] is invalid` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [init_global_variables](api.md#init-global-variables) | `[krd_tesis] is invalid` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [update_loan_history](api.md#update-loan-history) | `[p_tx_fid] is null at [loan_api.update_loan_history]` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_schedule_allignment](api.md#do-schedule-allignment) | `at [do_schedule_allignment] parametr [p_payment_amount] less than [0]` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_journal_control](api.md#do-journal-control) | `int_top_amount cant be negative!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_int_calculation](api.md#do-int-calculation) | `is_int_calc or is_pen_calc columns in krd_teklif_detay table is null! Please check...` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_journal_control](api.md#do-journal-control) | `main_top_amount cant be negative!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [loan_int_diff_operation](api.md#loan-int-diff-operation) | `original_amount or residual_amount or calc_amount or sum_residual_amount                                 or p_plan_int_amount or p_int_amount is negative` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_journal_control](api.md#do-journal-control) | `ovd_int_top_amount cant be negative!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_from_matrix](api.md#get-gl-acc-from-matrix) | `p_acc_type is invalid!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_loan_history](api.md#create-loan-history) | `p_app_oper_code not found in loan_operation_desc table!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_ovd_date](api.md#get-ovd-date), [get_ovd_date_old](api.md#get-ovd-date-old) | `p_calc_mode should be FOR_PEN_CALC - for penalty calculation, DEFAULT-for reporting` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_for_pen_calc](api.md#get-amount-for-pen-calc-2) | `p_for_spec_days must be Y or N!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_gl_acc_from_matrix](api.md#get-gl-acc-from-matrix) | `p_gl_base_type should be MAIN - for main account, OVD_MAIN - for overdue account!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_interest_calc_dates](api.md#get-interest-calc-dates), [get_interest_calc_dates_ex](api.md#get-interest-calc-dates-ex) | `p_int_calc_at param should be EOD or SOD!!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_overdrafts](api.md#create-overdrafts) | `p_oper_type should be CREATE_OVERDRAFT or CLOSE_LOAN` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_amount_for_pen_calc](api.md#get-amount-for-pen-calc-1) | `p_plan_type param can be MAIN , INT !` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_voucher_data_from_query](api.md#get-voucher-data-from-query) | `p_query can be null!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [get_voucher_data_from_query](api.md#get-voucher-data-from-query) | `p_result_type should be SINGLE_ROW or MULTI_ROW!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [recalculate_int_payment_plan](api.md#recalculate-int-payment-plan) | `p_schedule_update_type should be 3 or 4!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_journal_entry](api.md#do-journal-entry) | `p_trn_type must be CREATE or POST!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [create_loan_history](api.md#create-loan-history) | `p_trn_type must be I-insert, U-update, D-delete` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [do_create_tranche](api.md#do-create-tranche) | `p_trn_type should be CREATE - for create, DELETE - for delete` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [loan_int_diff_operation](api.md#loan-int-diff-operation) | `p_tx_fid or p_doc_no or p_acc_type or p_eod_sod cant be null!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [table_log_operation](api.md#table-log-operation) | `p_tx_fid or p_document_no parameters cant be null!` | Explicit application error message; consult method implementation for the exact triggering condition. |
| [post_int_amount_to_plan](api.md#post-int-amount-to-plan) | `p_with_tranche_info_yn shoul be Y - with tranche loans, N - for standart loans!` | Explicit application error message; consult method implementation for the exact triggering condition. |

## Error Propagation

The package uses application error helpers and Oracle exception handling in several operations. Generic `WHEN OTHERS` handlers are not individually documented because they do not, on their own, define a distinct business error contract.

Error codes and exact propagation semantics must not be inferred when the implementation of the shared error helper is unavailable.
