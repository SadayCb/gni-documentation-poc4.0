# LOAN_API — API Reference

[Back to Overview](README.md)

<a id="api-index"></a>
## API Index

### Loan operations and controls

- [get_loan_amount](#get-loan-amount)
- [get_trn_caller_id](#get-trn-caller-id)
- [get_offer_id](#get-offer-id)
- [is_online_offer](#is-online-offer)
- [do_loan_control (overload 1)](#do-loan-control-1)
- [do_loan_control (overload 2)](#do-loan-control-2)
- [do_loan_collateral_out](#do-loan-collateral-out)
- [do_commission_recognition](#do-commission-recognition)
- [do_guarantee_out](#do-guarantee-out)
- [do_loan_close_with_collateral_out](#do-loan-close-with-collateral-out)
- [do_non_cash_loan_close](#do-non-cash-loan-close)

### Accounting and accounts

- [get_voucher_data_from_query](#get-voucher-data-from-query)
- [get_gl_value](#get-gl-value)
- [get_gl_acc_active_passive](#get-gl-acc-active-passive)
- [get_gl_acc_from_matrix](#get-gl-acc-from-matrix)
- [get_account_feature](#get-account-feature)
- [do_journal_entry](#do-journal-entry)
- [create_journal_entries](#create-journal-entries)
- [create_account](#create-account)
- [get_new_acc](#get-new-acc)
- [do_journal_control](#do-journal-control)
- [change_account_status](#change-account-status)

### Payments and allocation

- [get_amount_by_range](#get-amount-by-range)
- [generate_allocated_payment_list](#generate-allocated-payment-list)
- [add_payment_details](#add-payment-details)
- [do_auto_payment](#do-auto-payment)

### Payment schedules and dates

- [post_int_amount_to_plan](#post-int-amount-to-plan)
- [get_formatted_grace_from_list](#get-formatted-grace-from-list)
- [get_grace_info](#get-grace-info)
- [get_commission_schedule](#get-commission-schedule)
- [add_months_for_loan](#add-months-for-loan)
- [get_next_plan_pym](#get-next-plan-pym)
- [get_plan_payment_amount](#get-plan-payment-amount)
- [get_plan_month_count](#get-plan-month-count)
- [get_plan_paid_month_count](#get-plan-paid-month-count)
- [get_plan_error](#get-plan-error)
- [get_annuity_amount](#get-annuity-amount)
- [get_pym_startdate](#get-pym-startdate)
- [is_payment_date](#is-payment-date)
- [recalculate_int_payment_plan](#recalculate-int-payment-plan)
- [do_plan_control](#do-plan-control)
- [do_schedule_allignment](#do-schedule-allignment)
- [do_com_schedule_allignment](#do-com-schedule-allignment)
- [get_incorrect_days](#get-incorrect-days)
- [get_incorrect_days_count](#get-incorrect-days-count)
- [get_schedule_from_memo](#get-schedule-from-memo)
- [get_standart_schedule](#get-standart-schedule)
- [get_annuity_schedule](#get-annuity-schedule)
- [get_special_schedule](#get-special-schedule)
- [get_created_schedule](#get-created-schedule)
- [create_schedule](#create-schedule)
- [update_payment_plan](#update-payment-plan)

### Interest, penalties and rates

- [get_amount_for_pen_calc (overload 1)](#get-amount-for-pen-calc-1)
- [get_interest_calc_info](#get-interest-calc-info)
- [get_interest_calc_dates](#get-interest-calc-dates)
- [get_interest_calc_dates_ex](#get-interest-calc-dates-ex)
- [get_basis_year_days_cnt](#get-basis-year-days-cnt)
- [loan_int_diff_operation](#loan-int-diff-operation)
- [get_delay_int_rate](#get-delay-int-rate)
- [get_amount_for_pen_calc (overload 2)](#get-amount-for-pen-calc-2)
- [do_int_calculation](#do-int-calculation)
- [do_overdue_transit_operation](#do-overdue-transit-operation)
- [do_loan_delay_int_rate_upd](#do-loan-delay-int-rate-upd)
- [get_flow_ratio_info](#get-flow-ratio-info)
- [get_stop_ratio_info](#get-stop-ratio-info)

### Delinquency and status

- [get_ovd_trs_oper_type](#get-ovd-trs-oper-type)
- [get_overdue_min_amount](#get-overdue-min-amount)
- [get_overdue_grace_days](#get-overdue-grace-days)
- [get_ovd_date](#get-ovd-date)
- [get_ovd_date_old](#get-ovd-date-old)
- [do_loan_status_control](#do-loan-status-control)
- [get_acc_type_by_status](#get-acc-type-by-status)

### Limits, tranches and overdrafts

- [evaluate_limit_amount](#evaluate-limit-amount)
- [do_create_tranche](#do-create-tranche)
- [create_overdrafts](#create-overdrafts)
- [get_new_ov_cont_no](#get-new-ov-cont-no)

### History, metadata and reversals

- [clear_addtional_data](#clear-addtional-data)
- [add_additional_group](#add-additional-group)
- [end_additional_group](#end-additional-group)
- [add_additional_info (overload 1)](#add-additional-info-1)
- [add_additional_info (overload 2)](#add-additional-info-2)
- [add_column_update (overload 1)](#add-column-update-1)
- [add_column_update (overload 2)](#add-column-update-2)
- [get_additional_info](#get-additional-info)
- [finalize_addtional_process](#finalize-addtional-process)
- [reverse_update](#reverse-update)
- [do_delete_operation](#do-delete-operation)
- [table_log_operation](#table-log-operation)
- [create_loan_history](#create-loan-history)
- [update_loan_history](#update-loan-history)
- [init_global_variables](#init-global-variables)

## Loan operations and controls

<a id="get-loan-amount"></a>

### get_loan_amount

**Purpose:** Returns loan amount information for the supplied inputs.

**Signature**

```sql
function get_loan_amount(p_doc_no      in varchar2,
                           p_amount_type in varchar2,
                           p_date        in date default glbl.getsysdate,
                           p_oper_type   in varchar2 default null)
    return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_amount_type` | IN | Amount type |
| `p_date` | IN | Date |
| `p_oper_type` | IN | Oper type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `O` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-trn-caller-id"></a>

### get_trn_caller_id

**Purpose:** Returns trn caller id information for the supplied inputs.

**Signature**

```sql
function get_trn_caller_id(p_oper_type in varchar2) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_OPERATION_DESC`.

**Dependencies**

- `LOAN_OPERATION_DESC` — READ.

**Errors**

- `Operation type` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-offer-id"></a>

### get_offer_id

**Purpose:** Returns offer id information for the supplied inputs.

**Signature**

```sql
Function get_offer_id(p_branch_id In Number Default Glbl.Getsube,
                        P_date      In Date Default Glbl.Getsysdate)
    Return Varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_id` | IN | Branch id |
| `P_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Modifies `KRD_TEKLIF_NO`.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `KRD_TEKLIF_NO` — INSERT, UPDATE.

[↑ Back to API Index](#api-index)

<a id="is-online-offer"></a>

### is_online_offer

**Purpose:** Returns online offer information for the supplied inputs.

**Signature**

```sql
function is_online_offer(p_memorandum_id varchar2) return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_memorandum_id` | IN | Memorandum id |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_SCOR_MAIN`.

**Dependencies**

- `KRD_SCOR_MAIN` — READ.

[↑ Back to API Index](#api-index)

<a id="do-loan-control-1"></a>

### do_loan_control — overload 1

**Purpose:** Performs loan control processing for the specified loan or scope.

**Signature**

```sql
procedure do_loan_control(p_oper_type varchar2 default null,
                            p_date      date default glbl.getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |
| `p_date` | IN | Date |

**Business Logic**

- Reads relevant data from `LOAN_EOD_CONTROL`, `KRD_TEKLIF_DETAY`.

**Dependencies**

- `LOAN_EOD_CONTROL` — READ.
- `KRD_TEKLIF_DETAY` — READ.
- `GNI_UTILITY` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-loan-control-2"></a>

### do_loan_control — overload 2

**Purpose:** Performs loan control processing for the specified loan or scope.

**Signature**

```sql
procedure do_loan_control(p_oper_type varchar2 default null,
                            p_date      date default glbl.getsysdate,
                            p_min_rowid rowid,
                            p_max_rowid rowid);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |
| `p_date` | IN | Date |
| `p_min_rowid` | IN | Min rowid |
| `p_max_rowid` | IN | Max rowid |

**Business Logic**

- Modifies `LOAN_EOD_CONTROL`.
- Reads relevant data from `KRD_TEKLIF_DETAY`, `LOAN_EOD_CONTROL_EXP`, `LOAN_OPERATION_HISTORY`.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `LOAN_EOD_CONTROL_EXP` — READ.
- `LOAN_OPERATION_HISTORY` — READ.
- `LOAN_EOD_CONTROL` — INSERT.
- `GLBL` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-loan-collateral-out"></a>

### do_loan_collateral_out

**Purpose:** Performs loan collateral out processing for the specified loan or scope.

**Signature**

```sql
procedure do_loan_collateral_out(p_doc_no in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |

**Business Logic**

- Modifies `KRD_SCOR_REAL_ESTATE_C`, `KRD_SCOR_AUTO_C`, `KRD_SCOR_ESYA_C`, `KRD_SCOR_EMANET_C` and related records.
- Reads relevant data from `CS_ACCOUNT`, `KRD_TEMINAT_TIP_PR`, `KRD_SCOR_REAL_ESTATE_C` and other referenced sources.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `KRD_TEMINAT_TIP_PR` — READ.
- `KRD_SCOR_REAL_ESTATE_C` — READ, UPDATE.
- `KRD_SCOR_AUTO_C` — READ, UPDATE.
- `KRD_SCOR_ESYA_C` — READ, UPDATE.
- `BLOKE_API` — referenced package or interface.
- `GLBL_CCY` — referenced package or interface.
- `GLBL_EOD` — referenced package or interface.
- `MM_ACCOUNTING#` — referenced package or interface.
- `PA_API#` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-commission-recognition"></a>

### do_commission_recognition

**Purpose:** Performs commission recognition processing for the specified loan or scope.

**Signature**

```sql
Procedure do_commission_recognition(p_doc_no varchar2 default null,
                                      Pdate    In Date Default Glbl.Getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `Pdate` | IN | Pdate |

**Business Logic**

- Modifies `KRD_KOM_EOD`.
- Reads relevant data from `KRD_KOM_PLAN_DETAY`, `KRD_TESIS`, `KRD_KOM_EOD`.

**Dependencies**

- `KRD_KOM_PLAN_DETAY` — READ.
- `KRD_TESIS` — READ.
- `KRD_KOM_EOD` — INSERT, READ, UPDATE.
- `GLBL_BAKIYE` — referenced package or interface.
- `GLBL_TARIH` — referenced package or interface.
- `KRD_EOD` — referenced package or interface.

**Errors**

- `This Program can run only last day of month!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-guarantee-out"></a>

### do_guarantee_out

**Purpose:** Performs guarantee out processing for the specified loan or scope.

**Signature**

```sql
Procedure do_guarantee_out(p_branch_id   In Number Default Null,
                             p_customer_no In Number Default Null,
                             p_loan_acc    In Number Default Null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_id` | IN | Branch id |
| `p_customer_no` | IN | Customer no |
| `p_loan_acc` | IN | Loan acc |

**Business Logic**

- Reads relevant data from `KRD_TESIS`.

**Dependencies**

- `KRD_TESIS` — READ.
- `APEX_KRD2220_0_API_P` — referenced package or interface.
- `GLBL_BAKIYE` — referenced package or interface.
- `KRD2220_0_API` — referenced package or interface.
- `TRN_BROKER` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-loan-close-with-collateral-out"></a>

### do_loan_close_with_collateral_out

**Purpose:** Performs loan close with collateral out processing for the specified loan or scope.

**Signature**

```sql
procedure do_Loan_Close_With_Collateral_Out(p_doc_no in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |

**Business Logic**

- Modifies `LOAN_EOD_AUTO_CLOSE`, `KRD_TEKLIF_DETAY`, `KRD_FON_VERILME`.
- Reads relevant data from `LOAN_PORTFOLIO_LITE`, `LOAN_EOD_AUTO_CLOSE`, `LOAN_TRANCHE_LIMIT_CHANGES_HISTORY`.
- Invokes journal-entry processing as part of the operation.
- Records or updates loan operation history.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `LOAN_PORTFOLIO_LITE` — READ.
- `LOAN_EOD_AUTO_CLOSE` — INSERT, READ.
- `LOAN_TRANCHE_LIMIT_CHANGES_HISTORY` — READ.
- `KRD_TEKLIF_DETAY` — UPDATE.
- `KRD_FON_VERILME` — UPDATE.
- `GLBL_EOD` — referenced package or interface.
- `GLBL_HESAP` — referenced package or interface.
- `TRN_BROKER` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-non-cash-loan-close"></a>

### do_non_cash_loan_close

**Purpose:** Performs non cash loan close processing for the specified loan or scope.

**Signature**

```sql
Procedure do_non_cash_loan_close(p_doc_no in varchar2,
                                   p_Date   In Date Default Glbl.Getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_Date` | IN | Date |

**Business Logic**

- Reads relevant data from `KRD_TESIS`, `CS_ACCOUNT`.

**Dependencies**

- `KRD_TESIS` — READ.
- `CS_ACCOUNT` — READ.
- `APEX_KRD2220_0_API_P` — referenced package or interface.
- `GLBL_BAKIYE` — referenced package or interface.
- `KRD2220_0_API` — referenced package or interface.
- `TRN_BROKER` — referenced package or interface.

**Errors**

- `Kreditde sehv:` (message fragment in source).

[↑ Back to API Index](#api-index)

## Accounting and accounts

<a id="get-voucher-data-from-query"></a>

### get_voucher_data_from_query

**Purpose:** Returns voucher data from query information for the supplied inputs.

**Signature**

```sql
function get_voucher_data_from_query(p_query       in varchar2,
                                       p_result_type in varchar2)
    return g_col_value_tab_map;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_query` | IN | Query |
| `p_result_type` | IN | Result type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `DBMS_SQL` — referenced package or interface.

**Errors**

- `p_query can be null!` (message fragment in source).
- `p_result_type should be SINGLE_ROW or MULTI_ROW!` (message fragment in source).
- `GROUP_CODE field is not defined in query or GROUP_CODE field is null!` (message fragment in source).
- `Result of query is empty!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-gl-value"></a>

### get_gl_value

**Purpose:** Returns gl value information for the supplied inputs.

**Signature**

```sql
function get_gl_value(p_parameter_name in varchar2) return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_parameter_name` | IN | Parameter name |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_GLOBAL_PARAMETERS_PR`.

**Dependencies**

- `LOAN_GLOBAL_PARAMETERS_PR` — READ.

**Errors**

- `Too many rows in search of parameter{` (message fragment in source).
- `Encountered error in search of parameter {` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-gl-acc-active-passive"></a>

### get_gl_acc_active_passive

**Purpose:** Returns gl acc active passive information for the supplied inputs.

**Signature**

```sql
function get_gl_acc_active_passive(p_acc_no in varchar2) return varchar2 result_cache;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_acc_no` | IN | Acc no |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `GL_ACCOUNT_DEFINE`.

**Dependencies**

- `GL_ACCOUNT_DEFINE` — READ.

**Errors**

- `Encountered more than one row in gl_account_define                               table in search of account_no:` (message fragment in source).
- `Encountered error in gl_account_define                               table in search of account_no:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-gl-acc-from-matrix"></a>

### get_gl_acc_from_matrix

**Purpose:** Returns gl acc from matrix information for the supplied inputs.

**Signature**

```sql
function get_gl_acc_from_matrix(p_product_code in number default null,
                                  p_cust_type    in number default null,
                                  p_period_id    in number default null,
                                  p_currency_id  in number default null,
                                  p_base_type    in varchar2,
                                  p_loan_doc_no  in varchar2 default null,
                                  p_acc_type     in varchar2) return varchar2 result_cache;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_product_code` | IN | Product code |
| `p_cust_type` | IN | Cust type |
| `p_period_id` | IN | Period id |
| `p_currency_id` | IN | Currency id |
| `p_base_type` | IN | Base type |
| `p_loan_doc_no` | IN | Loan doc no |
| `p_acc_type` | IN | Acc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`, `KRD_TEKLIF_DETAY`, `GL_URUN_HESAP_PR` and other referenced sources.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `KRD_TEKLIF_DETAY` — READ.
- `GL_URUN_HESAP_PR` — READ.
- `SP_URUN_PR` — READ.
- `GLBL_HESAP` — referenced package or interface.

**Errors**

- `p_gl_base_type should be MAIN - for main account, OVD_MAIN - for overdue account!` (message fragment in source).
- `No data found in gl_urun_hesap_pr table!` (message fragment in source).
- `Many rows found in gl_urun_hesap_pr table!` (message fragment in source).
- `p_acc_type is invalid!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-account-feature"></a>

### get_account_feature

**Purpose:** Returns account feature information for the supplied inputs.

**Signature**

```sql
function get_account_feature(p_branch_no   number,
                               p_account_no  number,
                               p_account_sub number)
    return cs_account.account_feature%type;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_no` | IN | Branch no |
| `p_account_no` | IN | Account no |
| `p_account_sub` | IN | Account sub |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`.

**Dependencies**

- `CS_ACCOUNT` — READ.

[↑ Back to API Index](#api-index)

<a id="do-journal-entry"></a>

### do_journal_entry

**Purpose:** Performs journal entry processing for the specified loan or scope.

**Signature**

```sql
Procedure do_journal_entry(p_entries_list  g_entries_list_tab,
                             p_trn_caller_id in number,
                             p_tx_fid        in out number,
                             p_trn_type      in varchar2,
                             p_is_eod        in varchar2 default 'Y');
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_entries_list` | IN | Entries list |
| `p_trn_caller_id` | IN | Trn caller id |
| `p_tx_fid` | IN OUT | Tx fid |
| `p_trn_type` | IN | Trn type |
| `p_is_eod` | IN | Is eod |

**Business Logic**

- Reads relevant data from `SS_MUH1201_0_LOG`.
- Invokes journal-entry processing as part of the operation.

**Dependencies**

- `SS_MUH1201_0_LOG` — READ.
- `MM_ACCOUNTING#` — referenced package or interface.
- `PA_API#` — referenced package or interface.
- `TRN_BROKER` — referenced package or interface.

**Errors**

- `p_trn_type must be CREATE or POST!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="create-journal-entries"></a>

### create_journal_entries

**Purpose:** Creates journal entries records or associated operational data.

**Signature**

```sql
procedure create_journal_entries(p_oper_type in varchar2,
                                   p_tx_fid    in number,
                                   p_trn_type  in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |
| `p_tx_fid` | IN | Tx fid |
| `p_trn_type` | IN | Trn type |

**Business Logic**

- Reads relevant data from `LOAN_OPERATION_DESC`, `LOAN_OPERATION_VOUCHER`, `SS_MUH1201_0_LOG`.
- Invokes journal-entry processing as part of the operation.

**Dependencies**

- `LOAN_OPERATION_DESC` — READ.
- `LOAN_OPERATION_VOUCHER` — READ.
- `SS_MUH1201_0_LOG` — READ.

**Errors**

- `No data found in loan_operation_desc!` (message fragment in source).
- `Too many rows found in loan_operation_desc!` (message fragment in source).
- `Query column:` (message fragment in source).
- `Voucher for the group_code:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="create-account"></a>

### create_account

**Purpose:** Creates account records or associated operational data.

**Signature**

```sql
procedure create_account(p_doc_no      in varchar2,
                           p_oper_type   in varchar2,
                           p_acc_type    in varchar2 default null,
                           p_tx_fid      in number,
                           p_created_acc out g_loan_accounts_tab);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_oper_type` | IN | Oper type |
| `p_acc_type` | IN | Acc type |
| `p_tx_fid` | IN | Tx fid |
| `p_created_acc` | OUT | Created acc |

**Business Logic**

- Modifies `KRD_TEKLIF_DETAY`, `KRD_TESIS`.
- Reads relevant data from `KRD_TEKLIF_DETAY`, `KRD_TESIS`, `SP_FAIZ_GUN_TANIM_PR` and other referenced sources.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ, UPDATE.
- `KRD_TESIS` — READ, UPDATE.
- `SP_FAIZ_GUN_TANIM_PR` — READ.
- `LOAN_ACC_TYPES_PR` — READ.
- `LOAN_ACCOUNTS` — READ.
- `GLBL_NAME` — referenced package or interface.
- `GLBL_TARIH` — referenced package or interface.
- `GNI_MESSAGE` — referenced package or interface.

**Errors**

- `Balance account for` (message fragment in source).
- `No data found in table loan_acc_types_pr with params p_acc_type:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-new-acc"></a>

### get_new_acc

**Purpose:** Returns new acc information for the supplied inputs.

**Signature**

```sql
function get_new_acc(p_branch_no       in number,
                       p_customer_no     in number,
                       p_balance_acc     in varchar2,
                       p_detail_code     in varchar2,
                       p_ccy_id          in number,
                       p_main_acc        in number default null,
                       p_cr_int_rate     in number default null,
                       p_dr_int_rate     in number default null,
                       p_com_int_rate    in number default null,
                       p_product_code    in number default null,
                       p_period_id       in number default null,
                       p_acc_description in varchar2,
                       p_loan_doc_no     in varchar2,
                       p_loan_acc_type   in varchar2,
                       p_tx_fid          in number) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_no` | IN | Branch no |
| `p_customer_no` | IN | Customer no |
| `p_balance_acc` | IN | Balance acc |
| `p_detail_code` | IN | Detail code |
| `p_ccy_id` | IN | Ccy id |
| `p_main_acc` | IN | Main acc |
| `p_cr_int_rate` | IN | Cr int rate |
| `p_dr_int_rate` | IN | Dr int rate |
| `p_com_int_rate` | IN | Com int rate |
| `p_product_code` | IN | Product code |
| `p_period_id` | IN | Period id |
| `p_acc_description` | IN | Acc description |
| `p_loan_doc_no` | IN | Loan doc no |
| `p_loan_acc_type` | IN | Loan acc type |
| `p_tx_fid` | IN | Tx fid |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_ACC_TYPES_PR`, `CS_ACCOUNT`.

**Dependencies**

- `LOAN_ACC_TYPES_PR` — READ.
- `CS_ACCOUNT` — READ.
- `GLBL_HESAP` — referenced package or interface.
- `GNI_MESSAGE` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-journal-control"></a>

### do_journal_control

**Purpose:** Performs journal control processing for the specified loan or scope.

**Signature**

```sql
procedure do_journal_control(p_branch_id   IN Number,
                               p_customer_no IN Number,
                               p_account_sub IN Number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_id` | IN | Branch id |
| `p_customer_no` | IN | Customer no |
| `p_account_sub` | IN | Account sub |

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`.

**Dependencies**

- `CS_ACCOUNT` — READ.

**Errors**

- `main_top_amount cant be negative!` (message fragment in source).
- `int_top_amount cant be negative!` (message fragment in source).
- `ovd_int_top_amount cant be negative!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="change-account-status"></a>

### change_account_status

**Purpose:** Change account status for the supplied inputs.

**Signature**

```sql
procedure change_account_status(p_doc_no in varchar2,
                                  p_status in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_status` | IN | Status |

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `CS_ACCOUNT`.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `CS_ACCOUNT` — READ.
- `GLBL_HESAP` — referenced package or interface.
- `LOAN_CATEGORY_API` — referenced package or interface.

**Errors**

- `Loan with doc_no:` (message fragment in source).
- `Only followings p_status are accepted O-open, C-close!` (message fragment in source).
- `Loan Status Not Found!` (message fragment in source).
- `Loan Status Has More Than 1 Value !` (message fragment in source).

[↑ Back to API Index](#api-index)

## Payments and allocation

<a id="get-amount-by-range"></a>

### get_amount_by_range

**Purpose:** Returns amount by range information for the supplied inputs.

**Signature**

```sql
function get_amount_by_range(p_oper_type    in varchar2,
                               p_acc_type     in varchar2,
                               p_tranche_type in varchar2 default null,
                               p_amount       in number) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |
| `p_acc_type` | IN | Acc type |
| `p_tranche_type` | IN | Tranche type |
| `p_amount` | IN | Amount |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_AMOUNT_RANGE_INFO`.

**Dependencies**

- `LOAN_AMOUNT_RANGE_INFO` — READ.

**Errors**

- `No data found in loan_amount_range_info table!` (message fragment in source).
- `Too many rows found in loan_amount_range_info table!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="generate-allocated-payment-list"></a>

### generate_allocated_payment_list

**Purpose:** Generates allocated payment list data based on the supplied inputs.

**Signature**

```sql
procedure generate_allocated_payment_list(p_doc_no                in varchar2,
                                            p_oper_type             in varchar2,
                                            p_pym_amount            in number,
                                            p_has_schedule_upd_type out varchar2,
                                            p_payment_list          out loan_api.g_loan_accounts_tab);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_oper_type` | IN | Oper type |
| `p_pym_amount` | IN | Pym amount |
| `p_has_schedule_upd_type` | OUT | Has schedule upd type |
| `p_payment_list` | OUT | Payment list |

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `O` — referenced package or interface.

**Errors**

- `Payment branch or customer or account is null Pymt_branch_no:` (message fragment in source).
- `Payment amount cant be more than balance amount!                             Please check amount of acc_type:` (message fragment in source).
- `Payment amount cant be negative!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="add-payment-details"></a>

### add_payment_details

**Purpose:** Adds payment details information to the relevant loan processing context.

**Signature**

```sql
procedure add_payment_details(p_doc_no                in varchar2,
                                p_has_schedule_upd_type out varchar2,
                                p_payment_list          in out loan_api.g_loan_accounts_tab);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_has_schedule_upd_type` | OUT | Has schedule upd type |
| `p_payment_list` | IN OUT | Payment list |

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `O` — referenced package or interface.

**Errors**

- `Can not find Acc_type : {` (message fragment in source).
- `Payment branch or customer or account is null Pymt_branch_no:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-auto-payment"></a>

### do_auto_payment

**Purpose:** Performs auto payment processing for the specified loan or scope.

**Signature**

```sql
Procedure do_Auto_Payment(p_min_id     number default null,
                            p_max_id     number default null,
                            p_doc_no     in varchar2 default null,
                            p_eod_sod    in varchar2 default 'E',
                            p_test_param in number default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_min_id` | IN | Min id |
| `p_max_id` | IN | Max id |
| `p_doc_no` | IN | Doc no |
| `p_eod_sod` | IN | Eod sod |
| `p_test_param` | IN | Test param |

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`, `KRD_TEKLIF_DETAY`, `EOD_PROGRAMS_EXCEPTION`.
- Contains an explicit `COMMIT`; callers should review transaction ownership.
- Contains an explicit `ROLLBACK` path.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.
- `KRD_TEKLIF_DETAY` — READ.
- `EOD_PROGRAMS_EXCEPTION` — READ.
- `APEX_KRD2204_0_API_P` — referenced package or interface.
- `APEX_KRD2204_2_API_P` — referenced package or interface.
- `APEX_KRD2204_7_API_P` — referenced package or interface.
- `GLBL_BAKIYE` — referenced package or interface.
- `GLBL_CCY` — referenced package or interface.

**Errors**

- `Auto payment type should be 1-Plan payment or 2-Off plan payment!` (message fragment in source).

[↑ Back to API Index](#api-index)

## Payment schedules and dates

<a id="post-int-amount-to-plan"></a>

### post_int_amount_to_plan

**Purpose:** Post int amount to plan for the supplied inputs.

**Signature**

```sql
procedure post_int_amount_to_plan(p_doc_no               in varchar2,
                                    p_tranche_no           in number,
                                    p_tx_fid               in number,
                                    p_acc_type             in varchar2,
                                    p_amount               in number,
                                    p_plan_date            in date,
                                    p_with_tranche_info_yn in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_tranche_no` | IN | Tranche no |
| `p_tx_fid` | IN | Tx fid |
| `p_acc_type` | IN | Acc type |
| `p_amount` | IN | Amount |
| `p_plan_date` | IN | Plan date |
| `p_with_tranche_info_yn` | IN | With tranche info yn |

**Business Logic**

- Modifies `LOAN_TRANCHE_PAYMENT_PLAN`, `LOAN_PAYMENT_PLAN`.
- Reads relevant data from `LOAN_ACC_TYPES_PR`, `LOAN_TRANCHE_PAYMENT_PLAN`, `LOAN_PAYMENT_PLAN`.
- Handles both standard and tranche-specific payment-plan data.

**Dependencies**

- `LOAN_ACC_TYPES_PR` — READ.
- `LOAN_TRANCHE_PAYMENT_PLAN` — READ, UPDATE.
- `LOAN_PAYMENT_PLAN` — READ, UPDATE.
- `LOAN_TRANCHE_API` — referenced package or interface.

**Errors**

- `Account type{` (message fragment in source).
- `Posting amounts is not allowed for this account type{` (message fragment in source).
- `p_with_tranche_info_yn shoul be Y - with tranche loans, N - for standart loans!` (message fragment in source).
- `Plan with acc_type {` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-formatted-grace-from-list"></a>

### get_formatted_grace_from_list

**Purpose:** Returns formatted grace from list information for the supplied inputs.

**Signature**

```sql
function get_formatted_grace_from_list(p_period_list in varchar2)
    return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_period_list` | IN | Period list |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

[↑ Back to API Index](#api-index)

<a id="get-grace-info"></a>

### get_grace_info

**Purpose:** Returns grace info information for the supplied inputs.

**Signature**

```sql
function get_grace_info(p_Doc_No          In Varchar2,
                          p_period_end_date in date,
                          p_acc_type        In Varchar2 default 'A',
                          p_info_type       in varchar2) Return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Doc_No` | IN | Doc no |
| `p_period_end_date` | IN | Period end date |
| `p_acc_type` | IN | Acc type |
| `p_info_type` | IN | Info type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.

[↑ Back to API Index](#api-index)

<a id="get-commission-schedule"></a>

### get_commission_schedule

**Purpose:** Returns commission schedule information for the supplied inputs.

**Signature**

```sql
Function get_commission_schedule(p_begin_date    In Date,
                                   p_end_date      In Date,
                                   p_amount        In Number,
                                   p_int_calc_type in varchar2)
    Return Krd_Kom_Plan_Tt
    Pipelined;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_begin_date` | IN | Begin date |
| `p_end_date` | IN | End date |
| `p_amount` | IN | Amount |
| `p_int_calc_type` | IN | Int calc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `L_BITME_TAR` — READ.
- `GLBL_FAIZ` — referenced package or interface.
- `GLBL_TARIH` — referenced package or interface.
- `GNI_MESSAGE` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="add-months-for-loan"></a>

### add_months_for_loan

**Purpose:** Adds months for loan information to the relevant loan processing context.

**Signature**

```sql
function add_months_for_loan(p_date   date,
                               p_months number,
                               p_day    number default null) return date;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |
| `p_months` | IN | Months |
| `p_day` | IN | Day |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `L_LAST_DATE` — READ.
- `L_DATE` — READ.

[↑ Back to API Index](#api-index)

<a id="get-next-plan-pym"></a>

### get_next_plan_pym

**Purpose:** Returns next plan pym information for the supplied inputs.

**Signature**

```sql
Function get_next_Plan_Pym(p_doc_no   In Varchar2,
                             P_date     In Date,
                             p_acc_type in varchar2) Return Number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `P_date` | IN | Date |
| `p_acc_type` | IN | Acc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.

[↑ Back to API Index](#api-index)

<a id="get-plan-payment-amount"></a>

### get_plan_payment_amount

**Purpose:** Returns plan payment amount information for the supplied inputs.

**Signature**

```sql
function get_plan_payment_amount(p_doc_no   in varchar2,
                                   p_date     in date default glbl.getsysdate,
                                   p_acc_type in varchar2 default null)
    return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_date` | IN | Date |
| `p_acc_type` | IN | Acc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `LOAN_PAYMENT_PLAN` — READ.
- `LOAN_TRANCHE_API` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-plan-month-count"></a>

### get_plan_month_count

**Purpose:** Returns plan month count information for the supplied inputs.

**Signature**

```sql
Function get_Plan_Month_Count(p_Start_Date    In Date,
                                p_End_Date      In Date,
                                p_int_calc_type varchar2 default '30/360 AZ',
                                p_work_days     varchar2 default 'Y',
                                p_pymt_day      number default null)
    Return Number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Start_Date` | IN | Start date |
| `p_End_Date` | IN | End date |
| `p_int_calc_type` | IN | Int calc type |
| `p_work_days` | IN | Work days |
| `p_pymt_day` | IN | Pymt day |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `GLBL_FAIZ` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-plan-paid-month-count"></a>

### get_plan_paid_month_count

**Purpose:** Returns plan paid month count information for the supplied inputs.

**Signature**

```sql
function get_plan_paid_month_count(p_doc_no in varchar2,
                                     p_term   in number,
                                     p_date   in date) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_term` | IN | Term |
| `p_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

[↑ Back to API Index](#api-index)

<a id="get-plan-error"></a>

### get_plan_error

**Purpose:** Returns plan error information for the supplied inputs.

**Signature**

```sql
Function get_plan_error(p_doc_no varchar2,
                          p_date   date default glbl.getsysdate)
    return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `GLBL` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-annuity-amount"></a>

### get_annuity_amount

**Purpose:** Returns annuity amount information for the supplied inputs.

**Signature**

```sql
Function get_Annuity_Amount(p_Doc_No      In Varchar2,
                              p_return_type In varchar2 default 'NO_ZERO')
    Return Number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Doc_No` | IN | Doc no |
| `p_return_type` | IN | Return type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.

[↑ Back to API Index](#api-index)

<a id="get-pym-startdate"></a>

### get_pym_startdate

**Purpose:** Returns pym startdate information for the supplied inputs.

**Signature**

```sql
Function get_Pym_Startdate(p_Doc_No          In Varchar2,
                             p_pymt_date       In Date,
                             p_pymt_day        In Number,
                             p_pymt_period     In Number,
                             p_acc_type        In varchar2,
                             p_loan_end_Date   in date,
                             p_check_is_closed in varchar2 default 'Y')
    Return Date;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Doc_No` | IN | Doc no |
| `p_pymt_date` | IN | Pymt date |
| `p_pymt_day` | IN | Pymt day |
| `p_pymt_period` | IN | Pymt period |
| `p_acc_type` | IN | Acc type |
| `p_loan_end_Date` | IN | Loan end date |
| `p_check_is_closed` | IN | Check is closed |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.
- `GLBL_FAIZ` — referenced package or interface.
- `GLBL_TARIH` — referenced package or interface.
- `GNI_MESSAGE` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="is-payment-date"></a>

### is_payment_date

**Purpose:** Returns payment date information for the supplied inputs.

**Signature**

```sql
Function is_Payment_Date(p_Document_No In Varchar2, p_Date Date)
    Return Varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Document_No` | IN | Document no |
| `p_Date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.
- `GLBL_TARIH` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="recalculate-int-payment-plan"></a>

### recalculate_int_payment_plan

**Purpose:** Recalculate int payment plan for the supplied inputs.

**Signature**

```sql
procedure recalculate_int_payment_plan(p_doc_no               in varchar2,
                                         p_acc_type             in varchar2,
                                         p_main_amount          in number,
                                         p_INT_RATIO            in number,
                                         p_int_calc_type        in varchar2,
                                         p_schedule_update_type in number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_acc_type` | IN | Acc type |
| `p_main_amount` | IN | Main amount |
| `p_INT_RATIO` | IN | Int ratio |
| `p_int_calc_type` | IN | Int calc type |
| `p_schedule_update_type` | IN | Schedule update type |

**Business Logic**

- Modifies `LOAN_PAYMENT_PLAN`.
- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ, UPDATE.
- `GLBL_FAIZ` — referenced package or interface.

**Errors**

- `p_schedule_update_type should be 3 or 4!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-plan-control"></a>

### do_plan_control

**Purpose:** Performs plan control processing for the specified loan or scope.

**Signature**

```sql
procedure do_plan_control(p_document_no in varchar2,
                            p_date        date default glbl.getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_document_no` | IN | Document no |
| `p_date` | IN | Date |

**Business Logic**

- Reads relevant data from `LOAN_EOD_CONTROL_EXP`.

**Dependencies**

- `LOAN_EOD_CONTROL_EXP` — READ.

[↑ Back to API Index](#api-index)

<a id="do-schedule-allignment"></a>

### do_schedule_allignment

**Purpose:** Performs schedule allignment processing for the specified loan or scope.

**Signature**

```sql
Procedure do_schedule_allignment(p_doc_no         In Varchar2,
                                   p_payment_amount In Number,
                                   p_acc_type       In Varchar2,
                                   p_date           In Date default glbl.getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_payment_amount` | IN | Payment amount |
| `p_acc_type` | IN | Acc type |
| `p_date` | IN | Date |

**Business Logic**

- Modifies `LOAN_PAYMENT_PLAN`.
- Reads relevant data from `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ, UPDATE.

**Errors**

- `at [do_schedule_allignment] parametr [p_payment_amount] less than [0]` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-com-schedule-allignment"></a>

### do_com_schedule_allignment

**Purpose:** Performs com schedule allignment processing for the specified loan or scope.

**Signature**

```sql
Procedure do_com_schedule_allignment(p_doc_no      In Varchar2,
                                       p_option_code In Varchar2,
                                       p_amount      In Number,
                                       p_plan_type   In Varchar2,
                                       p_mig_status  In Number Default 0);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_option_code` | IN | Option code |
| `p_amount` | IN | Amount |
| `p_plan_type` | IN | Plan type |
| `p_mig_status` | IN | Mig status |

**Business Logic**

- Modifies `KRD_KOM_PLAN_DETAY`.
- Reads relevant data from `KRD_TESIS`, `KRD_KOM_PLAN_DETAY`.

**Dependencies**

- `KRD_TESIS` — READ.
- `KRD_KOM_PLAN_DETAY` — READ, UPDATE.
- `GLOG` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-incorrect-days"></a>

### get_incorrect_days

**Purpose:** Returns incorrect days information for the supplied inputs.

**Signature**

```sql
function get_incorrect_days(p_date date) return NUMBER_TT
    pipelined;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

[↑ Back to API Index](#api-index)

<a id="get-incorrect-days-count"></a>

### get_incorrect_days_count

**Purpose:** Returns incorrect days count information for the supplied inputs.

**Signature**

```sql
function get_incorrect_days_count(p_date date) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

[↑ Back to API Index](#api-index)

<a id="get-schedule-from-memo"></a>

### get_schedule_from_memo

**Purpose:** Returns schedule from memo information for the supplied inputs.

**Signature**

```sql
function get_schedule_from_memo(p_memorandum_id varchar2,
                                  p_int_ratio     number,
                                  p_int_calc_type varchar2,
                                  p_int_amount    number) return SCHEDULE_TT
    pipelined;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_memorandum_id` | IN | Memorandum id |
| `p_int_ratio` | IN | Int ratio |
| `p_int_calc_type` | IN | Int calc type |
| `p_int_amount` | IN | Int amount |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_SCOR_ODEME_PLAN`.

**Dependencies**

- `KRD_SCOR_ODEME_PLAN` — READ.
- `GLBL_FAIZ` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-standart-schedule"></a>

### get_standart_schedule

**Purpose:** Returns standart schedule information for the supplied inputs.

**Signature**

```sql
function get_standart_schedule(p_begin_date          date default glbl.getsysdate,
                                 p_main_pymt_date      date,
                                 p_int_pymt_date       date,
                                 p_pymt_day            number default null,
                                 p_end_date            date,
                                 p_offer_amount        number,
                                 p_ovd_main_amount     number default 0,
                                 p_int_calc_type       varchar2,
                                 p_main_grace_period   varchar2 default null,
                                 p_int_grace_period    varchar2 default null,
                                 p_remain_int_amount   number default 0,
                                 p_min_main_pay_amount number default null,
                                 p_calc_int_in_grace   varchar2 default 'Y',
                                 p_work_days           varchar2 default 'Y',
                                 
                                 p_loan_flow_rate_tab LOAN_FLOW_RATE_TAB default null,
                                 p_loan_stop_rate_tab LOAN_STOP_RATE_TAB default null,
                                 p_special_dates      loan_special_dates_tab default null)
    return SCHEDULE_TT
    pipelined;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_begin_date` | IN | Begin date |
| `p_main_pymt_date` | IN | Main pymt date |
| `p_int_pymt_date` | IN | Int pymt date |
| `p_pymt_day` | IN | Pymt day |
| `p_end_date` | IN | End date |
| `p_offer_amount` | IN | Offer amount |
| `p_ovd_main_amount` | IN | Ovd main amount |
| `p_int_calc_type` | IN | Int calc type |
| `p_main_grace_period` | IN | Main grace period |
| `p_int_grace_period` | IN | Int grace period |
| `p_remain_int_amount` | IN | Remain int amount |
| `p_min_main_pay_amount` | IN | Min main pay amount |
| `p_calc_int_in_grace` | IN | Calc int in grace |
| `p_work_days` | IN | Work days |
| `p_loan_flow_rate_tab` | IN | Loan flow rate tab |
| `p_loan_stop_rate_tab` | IN | Loan stop rate tab |
| `p_special_dates` | IN | Special dates |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

[↑ Back to API Index](#api-index)

<a id="get-annuity-schedule"></a>

### get_annuity_schedule

**Purpose:** Returns annuity schedule information for the supplied inputs.

**Signature**

```sql
function get_annuity_schedule(p_begin_date      date,
                                p_main_pymt_date  date,
                                p_int_pymt_date   date,
                                p_pymt_day        number default null,
                                p_end_date        date,
                                p_offer_amount    number,
                                p_ovd_main_amount number default 0,
                                p_int_calc_type   varchar2,
                                
                                p_main_grace_period varchar2 default null,
                                p_int_grace_period  varchar2 default null,
                                
                                p_annuity_amount     number default null,
                                p_max_annuity_amount number default null,
                                p_remain_int_amount  number default 0,
                                
                                p_work_days         varchar2 default 'Y',
                                p_own_annuity       varchar2 default 'N',
                                p_calc_int_in_grace varchar2 default 'Y',
                                p_is_mortgage       varchar2 default 'N',
                                
                                p_max_iteration number default null,
                                
                                p_rest_main_pay_amount number default null,
                                p_rest_main_pay_months number default null,
                                
                                p_loan_flow_rate_tab LOAN_FLOW_RATE_TAB default null,
                                p_loan_stop_rate_tab LOAN_STOP_RATE_TAB default null,
                                p_special_dates      loan_special_dates_tab default null)
    return SCHEDULE_TT
    pipelined;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_begin_date` | IN | Begin date |
| `p_main_pymt_date` | IN | Main pymt date |
| `p_int_pymt_date` | IN | Int pymt date |
| `p_pymt_day` | IN | Pymt day |
| `p_end_date` | IN | End date |
| `p_offer_amount` | IN | Offer amount |
| `p_ovd_main_amount` | IN | Ovd main amount |
| `p_int_calc_type` | IN | Int calc type |
| `p_main_grace_period` | IN | Main grace period |
| `p_int_grace_period` | IN | Int grace period |
| `p_annuity_amount` | IN | Annuity amount |
| `p_max_annuity_amount` | IN | Max annuity amount |
| `p_remain_int_amount` | IN | Remain int amount |
| `p_work_days` | IN | Work days |
| `p_own_annuity` | IN | Own annuity |
| `p_calc_int_in_grace` | IN | Calc int in grace |
| `p_is_mortgage` | IN | Is mortgage |
| `p_max_iteration` | IN | Max iteration |
| `p_rest_main_pay_amount` | IN | Rest main pay amount |
| `p_rest_main_pay_months` | IN | Rest main pay months |
| `p_loan_flow_rate_tab` | IN | Loan flow rate tab |
| `p_loan_stop_rate_tab` | IN | Loan stop rate tab |
| `p_special_dates` | IN | Special dates |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `GLBL_FAIZ` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-special-schedule"></a>

### get_special_schedule

**Purpose:** Returns special schedule information for the supplied inputs.

**Signature**

```sql
Procedure get_special_schedule(p_doc_no             In Varchar2,
                                 p_begin_date         in Date Default Glbl.Getsysdate,
                                 p_offer_amount       In Number,
                                 p_int_ratio          In Number,
                                 p_int_calc_type      in varchar2,
                                 p_calc_int_int_grace in varchar2,
                                 p_annuity_amount     in Number Default Null,
                                 p_remain_int_amount  in number default 0);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_begin_date` | IN | Begin date |
| `p_offer_amount` | IN | Offer amount |
| `p_int_ratio` | IN | Int ratio |
| `p_int_calc_type` | IN | Int calc type |
| `p_calc_int_int_grace` | IN | Calc int int grace |
| `p_annuity_amount` | IN | Annuity amount |
| `p_remain_int_amount` | IN | Remain int amount |

**Business Logic**

- Modifies `ODEME_PLAN_TMP2`.
- Reads relevant data from `ODEME_PLAN_TMP2`.

**Dependencies**

- `ODEME_PLAN_TMP2` — READ, UPDATE.
- `GLBL_FAIZ` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-created-schedule"></a>

### get_created_schedule

**Purpose:** Returns created schedule information for the supplied inputs.

**Signature**

```sql
Procedure get_created_schedule(p_fid number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_fid` | IN | Fid |

**Business Logic**

- Reads relevant data from `CREATE_SCHEDULE_PARAMETRS`.

**Dependencies**

- `CREATE_SCHEDULE_PARAMETRS` — READ.
- `APEX_JSON` — referenced package or interface.

**Errors**

- `No record found for fid =` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="create-schedule"></a>

### create_schedule

**Purpose:** Creates schedule records or associated operational data.

**Signature**

```sql
procedure create_schedule(p_schedule_no          number,
                            p_coll_name            varchar2 default null,
                            p_fk_id                number default null,
                            p_doc_no               varchar2 default 'XXX',
                            p_memorandum_id        varchar2 default null,
                            p_customer_no          number default null,
                            p_tx_fid               number default null,
                            p_begin_date           date default glbl.getsysdate,
                            p_last_int_Calc_Date   date default glbl.getsysdate - 1,
                            p_main_pymt_date       date,
                            p_int_pymt_date        date,
                            p_pymt_day             number default null,
                            p_end_date             date,
                            p_offer_amount         number,
                            p_ovd_main_amount      number default 0,
                            p_int_ratio            number,
                            p_int_calc_type        varchar2,
                            p_annuity_amount       number default null,
                            p_max_annuity_amount   number default null,
                            p_min_main_pay_amount  number default null,
                            p_remain_int_amount    number default 0,
                            p_main_grace_period    varchar2 default null,
                            p_int_grace_period     varchar2 default null,
                            p_main_pymt_period     number default 1,
                            p_int_pymt_period      number default 1,
                            p_product_code         number default null,
                            p_same_annuity         varchar2 default 'N',
                            p_calc_int_in_grace    varchar2 default 'Y',
                            p_return_type          varchar2 default 'NO_ZERO',
                            p_rest_main_pay_amount number default null,
                            p_rest_main_pay_months number default null,
                            p_loan_flow_rate_tab   LOAN_FLOW_RATE_TAB default null,
                            p_loan_stop_rate_tab   LOAN_STOP_RATE_TAB default null,
                            p_special_dates        loan_special_dates_tab default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_schedule_no` | IN | Schedule no |
| `p_coll_name` | IN | Coll name |
| `p_fk_id` | IN | Fk id |
| `p_doc_no` | IN | Doc no |
| `p_memorandum_id` | IN | Memorandum id |
| `p_customer_no` | IN | Customer no |
| `p_tx_fid` | IN | Tx fid |
| `p_begin_date` | IN | Begin date |
| `p_last_int_Calc_Date` | IN | Last int calc date |
| `p_main_pymt_date` | IN | Main pymt date |
| `p_int_pymt_date` | IN | Int pymt date |
| `p_pymt_day` | IN | Pymt day |
| `p_end_date` | IN | End date |
| `p_offer_amount` | IN | Offer amount |
| `p_ovd_main_amount` | IN | Ovd main amount |
| `p_int_ratio` | IN | Int ratio |
| `p_int_calc_type` | IN | Int calc type |
| `p_annuity_amount` | IN | Annuity amount |
| `p_max_annuity_amount` | IN | Max annuity amount |
| `p_min_main_pay_amount` | IN | Min main pay amount |
| `p_remain_int_amount` | IN | Remain int amount |
| `p_main_grace_period` | IN | Main grace period |
| `p_int_grace_period` | IN | Int grace period |
| `p_main_pymt_period` | IN | Main pymt period |
| `p_int_pymt_period` | IN | Int pymt period |
| `p_product_code` | IN | Product code |
| `p_same_annuity` | IN | Same annuity |
| `p_calc_int_in_grace` | IN | Calc int in grace |
| `p_return_type` | IN | Return type |
| `p_rest_main_pay_amount` | IN | Rest main pay amount |
| `p_rest_main_pay_months` | IN | Rest main pay months |
| `p_loan_flow_rate_tab` | IN | Loan flow rate tab |
| `p_loan_stop_rate_tab` | IN | Loan stop rate tab |
| `p_special_dates` | IN | Special dates |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

[↑ Back to API Index](#api-index)

<a id="update-payment-plan"></a>

### update_payment_plan

**Purpose:** Updates payment plan information for the specified context.

**Signature**

```sql
PROCEDURE UPDATE_PAYMENT_PLAN(
                              P_DOC_NO             varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `P_DOC_NO` | IN | Doc no |

**Business Logic**

- Modifies `IBS.ONLINE_CRD_BLOCK`, `GAIA.KRD_TEKLIF_DETAY`, `LOAN_TEMPORARY_PAYMENT_PLAN`, `LOAN_PAYMENT_PLAN` and related records.
- Reads relevant data from `IBS.ONLINE_CRD_BLOCK`, `GAIA.KRD_TEKLIF_DETAY`, `L_BEGIN_DATE` and other referenced sources.
- Records or updates loan operation history.

**Dependencies**

- `IBS.ONLINE_CRD_BLOCK` — READ, UPDATE.
- `GAIA.KRD_TEKLIF_DETAY` — READ, UPDATE.
- `L_BEGIN_DATE` — READ.
- `ODEME_PLAN_TMP` — READ.
- `LOAN_TEMPORARY_PAYMENT_PLAN` — INSERT, READ.
- `API_CALENDAR` — referenced package or interface.
- `TRN_BROKER` — referenced package or interface.

**Errors**

- `This operation cannot be initialized when [with_tranche_info_yn] = ''Y''` (message fragment in source).
- `Update payment plan block ->` (message fragment in source).

[↑ Back to API Index](#api-index)

## Interest, penalties and rates

<a id="get-amount-for-pen-calc-1"></a>

### get_amount_for_pen_calc — overload 1

**Purpose:** Returns amount for pen calc information for the supplied inputs.

**Signature**

```sql
function get_amount_for_pen_calc(p_date                    in date,
                                   p_doc_no                  in varchar2,
                                   p_ovd_balance             in number,
                                   p_is_pen_calc_on_int      in varchar2,
                                   p_is_exclude_coll_amount  in varchar2,
                                   p_overdue_min_amount_main in number,
                                   p_loan_end_date           in date)
    return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |
| `p_doc_no` | IN | Doc no |
| `p_ovd_balance` | IN | Ovd balance |
| `p_is_pen_calc_on_int` | IN | Is pen calc on int |
| `p_is_exclude_coll_amount` | IN | Is exclude coll amount |
| `p_overdue_min_amount_main` | IN | Overdue min amount main |
| `p_loan_end_date` | IN | Loan end date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`, `LOAN_ACC_TYPES_PR`, `KRD_GUARANTEE_MAIN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.
- `LOAN_ACC_TYPES_PR` — READ.
- `KRD_GUARANTEE_MAIN` — READ.

**Errors**

- `Overdue int in plan or ovd_balance amount for penalty calculation is negative!` (message fragment in source).
- `p_plan_type param can be MAIN , INT !` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-interest-calc-info"></a>

### get_interest_calc_info

**Purpose:** Returns interest calc info information for the supplied inputs.

**Signature**

```sql
procedure get_interest_calc_info(p_last_calc_date       in date,
                                   p_pymt_day             in number,
                                   p_trn_date             in date,
                                   p_int_calc_type        in varchar2,
                                   p_rate_type            in varchar2,
                                   p_int_rate_periodicity in varchar2,
                                   p_calc_day_count       out number,
                                   p_year_day_count       out number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_last_calc_date` | IN | Last calc date |
| `p_pymt_day` | IN | Pymt day |
| `p_trn_date` | IN | Trn date |
| `p_int_calc_type` | IN | Int calc type |
| `p_rate_type` | IN | Rate type |
| `p_int_rate_periodicity` | IN | Int rate periodicity |
| `p_calc_day_count` | OUT | Calc day count |
| `p_year_day_count` | OUT | Year day count |

**Business Logic**

- Reads relevant data from `LOAN_INT_CALC_TYPES_PR`.

**Dependencies**

- `LOAN_INT_CALC_TYPES_PR` — READ.

**Errors**

- `Payment day cant be null, please check!` (message fragment in source).
- `Transaction date cant be less than last calculation date!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-interest-calc-dates"></a>

### get_interest_calc_dates

**Purpose:** Returns interest calc dates information for the supplied inputs.

**Signature**

```sql
function get_interest_calc_dates(p_last_calc_access_date in date,
                                   p_eod_sod               in varchar2,
                                   p_int_calc_at           in varchar2)
    return loan_api.g_date_tab_type;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_last_calc_access_date` | IN | Last calc access date |
| `p_eod_sod` | IN | Eod sod |
| `p_int_calc_at` | IN | Int calc at |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `GLBL_TARIH` — referenced package or interface.

**Errors**

- `p_int_calc_at param should be EOD or SOD!!` (message fragment in source).
- `P_EOD_SOD param should be E - EOD or S - SOD!!` (message fragment in source).
- `Interest calculation should be done at EOD or SOD!!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-interest-calc-dates-ex"></a>

### get_interest_calc_dates_ex

**Purpose:** Returns interest calc dates ex information for the supplied inputs.

**Signature**

```sql
function get_interest_calc_dates_ex(p_date        in date,
                                      p_eod_sod     in varchar2,
                                      p_int_calc_at in varchar2)
    return g_date_tab_type;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |
| `p_eod_sod` | IN | Eod sod |
| `p_int_calc_at` | IN | Int calc at |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Calculates or retrieves the function result using the supplied parameters.

**Dependencies**

- `GLBL_TARIH` — referenced package or interface.

**Errors**

- `p_int_calc_at param should be EOD or SOD!!` (message fragment in source).
- `P_EOD_SOD param should be E - EOD or S - SOD!!` (message fragment in source).
- `Interest calculation should be done at EOD or SOD!!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-basis-year-days-cnt"></a>

### get_basis_year_days_cnt

**Purpose:** Returns basis year days cnt information for the supplied inputs.

**Signature**

```sql
function get_basis_year_days_cnt(p_int_calc_type in varchar2,
                                   p_date          in date) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_int_calc_type` | IN | Int calc type |
| `p_date` | IN | Date |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_INT_CALC_TYPES_PR`.

**Dependencies**

- `LOAN_INT_CALC_TYPES_PR` — READ.

[↑ Back to API Index](#api-index)

<a id="loan-int-diff-operation"></a>

### loan_int_diff_operation

**Purpose:** Loan int diff operation for the supplied inputs.

**Signature**

```sql
procedure loan_int_diff_operation(p_trn_date        in date,
                                    p_oper_type       in varchar2,
                                    p_trn_type        in varchar2,
                                    p_doc_no          in varchar2,
                                    p_acc_type        in varchar2,
                                    p_source_acc_type in varchar2,
                                    p_tx_fid          number,
                                    p_original_amount in number,
                                    p_eod_sod         in varchar2,
                                    p_payment_date    in date,
                                    p_plan_int_amount in number,
                                    p_int_amount      in number,
                                    p_calc_amount     out number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_trn_date` | IN | Trn date |
| `p_oper_type` | IN | Oper type |
| `p_trn_type` | IN | Trn type |
| `p_doc_no` | IN | Doc no |
| `p_acc_type` | IN | Acc type |
| `p_source_acc_type` | IN | Source acc type |
| `p_tx_fid` | IN | Tx fid |
| `p_original_amount` | IN | Original amount |
| `p_eod_sod` | IN | Eod sod |
| `p_payment_date` | IN | Payment date |
| `p_plan_int_amount` | IN | Plan int amount |
| `p_int_amount` | IN | Int amount |
| `p_calc_amount` | OUT | Calc amount |

**Business Logic**

- Modifies `LOAN_INT_CALCULATION_DIFF_HISTORY`.
- Reads relevant data from `LOAN_INT_CALCULATION_DIFF_HISTORY`.

**Dependencies**

- `LOAN_INT_CALCULATION_DIFF_HISTORY` — DELETE, INSERT, READ, UPDATE.
- `GLBL` — referenced package or interface.

**Errors**

- `p_tx_fid or p_doc_no or p_acc_type or p_eod_sod cant be null!` (message fragment in source).
- `original_amount or residual_amount or calc_amount or sum_residual_amount                                 or p_plan_int_amount or p_int_amount is negative` (message fragment in source).
- `Operation type must be INS, OPEN, CLOSE!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-delay-int-rate"></a>

### get_delay_int_rate

**Purpose:** Returns delay int rate information for the supplied inputs.

**Signature**

```sql
Function Get_Delay_Int_Rate(p_Loan_Id    In Varchar2,
                              p_Delay_Type In Varchar2) Return Number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Loan_Id` | IN | Loan id |
| `p_Delay_Type` | IN | Delay type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.

[↑ Back to API Index](#api-index)

<a id="get-amount-for-pen-calc-2"></a>

### get_amount_for_pen_calc — overload 2

**Purpose:** Returns amount for pen calc information for the supplied inputs.

**Signature**

```sql
Function get_amount_for_pen_calc(p_doc_no        In Varchar2,
                                   P_date          In Date,
                                   p_for_spec_days in varchar2 default 'N',
                                   p_int_calc_type in varchar2 default null)
    Return Number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `P_date` | IN | Date |
| `p_for_spec_days` | IN | For spec days |
| `p_int_calc_type` | IN | Int calc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_SPECIAL_DAYS_PR`, `LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_SPECIAL_DAYS_PR` — READ.
- `LOAN_PAYMENT_PLAN` — READ.
- `GLBL_FAIZ` — referenced package or interface.

**Errors**

- `Too many rows in loan_special_days_pr for date:` (message fragment in source).
- `p_for_spec_days must be Y or N!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-int-calculation"></a>

### do_int_calculation

**Purpose:** Performs int calculation processing for the specified loan or scope.

**Signature**

```sql
procedure do_int_calculation(p_min_id  number default 0,
                               p_max_id  number default 999999999,
                               p_doc_no  in varchar2 default null,
                               p_eod_sod in varchar2 default 'E',
                               p_date    in date default glbl.getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_min_id` | IN | Min id |
| `p_max_id` | IN | Max id |
| `p_doc_no` | IN | Doc no |
| `p_eod_sod` | IN | Eod sod |
| `p_date` | IN | Date |

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `EOD_PROGRAMS_EXCEPTION`, `LOAN_STOP_RATIO_INFO` and other referenced sources.
- Invokes journal-entry processing as part of the operation.
- Records or updates loan operation history.
- Contains an explicit `COMMIT`; callers should review transaction ownership.
- Contains an explicit `ROLLBACK` path.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `EOD_PROGRAMS_EXCEPTION` — READ.
- `LOAN_STOP_RATIO_INFO` — READ.
- `CS_ACCOUNT` — READ.
- `LOAN_FLOW_RATIO_INFO` — READ.
- `GLBL_FAIZ` — referenced package or interface.
- `GLBL_TARIH` — referenced package or interface.
- `GNI_UTILITY` — referenced package or interface.
- `LA` — referenced package or interface.
- `LOAN_REPORT_API` — referenced package or interface.

**Errors**

- `Int calculation has not finished yet for loans without transit process!` (message fragment in source).
- `is_int_calc or is_pen_calc columns in krd_teklif_detay table is null! Please check...` (message fragment in source).
- `Product code not found in pkrd_turkod_pr table,                    pls check 22401 app for this loan product!` (message fragment in source).
- `Not working day may be 1 or 2, please check 22401 app,                                        for product code:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-overdue-transit-operation"></a>

### do_overdue_transit_operation

**Purpose:** Performs overdue transit operation processing for the specified loan or scope.

**Signature**

```sql
Procedure do_overdue_transit_operation(p_min_id number default null,
                                         p_max_id number default null,
                                         p_doc_no in varchar2 default null,
                                         p_date   in date default glbl.getsysdate);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_min_id` | IN | Min id |
| `p_max_id` | IN | Max id |
| `p_doc_no` | IN | Doc no |
| `p_date` | IN | Date |

**Business Logic**

- Modifies `LOAN_PAYMENT_PLAN`, `KRD_TEKLIF_DETAY`.
- Reads relevant data from `LOAN_OVERDUE_TRANSIT_QUEUE`, `CS_ACCOUNT`, `LOAN_OVERDUE_MAPPING` and other referenced sources.
- Invokes journal-entry processing as part of the operation.
- Records or updates loan operation history.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `LOAN_OVERDUE_TRANSIT_QUEUE` — READ.
- `CS_ACCOUNT` — READ.
- `LOAN_OVERDUE_MAPPING` — READ.
- `LOAN_PAYMENT_PLAN` — INSERT, READ, UPDATE.
- `KRD_TEKLIF_DETAY` — UPDATE.
- `CL` — referenced package or interface.
- `CR` — referenced package or interface.
- `GNI_UTILITY` — referenced package or interface.
- `LOAN_REPORT_API` — referenced package or interface.

**Errors**

- `Loan product code not found in pkrd_turkod_pr table!` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-loan-delay-int-rate-upd"></a>

### do_loan_delay_int_rate_upd

**Purpose:** Performs loan delay int rate upd processing for the specified loan or scope.

**Signature**

```sql
Procedure do_Loan_Delay_Int_Rate_Upd;
```

**Business Logic**

- Modifies `CS_ACCOUNT`.
- Reads relevant data from `KRD_TESIS`.

**Dependencies**

- `KRD_TESIS` — READ.
- `CS_ACCOUNT` — UPDATE.

**Errors**

- `Gecikme Faizi 0-dan ferqli oldugu halda son gecikme faizi 0-dir!` (message fragment in source).
- `Kreditde sehv:` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-flow-ratio-info"></a>

### get_flow_ratio_info

**Purpose:** Returns flow ratio info information for the supplied inputs.

**Signature**

```sql
FUNCTION get_flow_ratio_info(p_doc_no    VARCHAR2,
                               p_date      DATE DEFAULT glbl.getsysdate,
                               p_full_info varchar2 default 'N')
    RETURN LOAN_FLOW_RATE_TAB;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_date` | IN | Date |
| `p_full_info` | IN | Full info |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_FLOW_RATIO_INFO`.

**Dependencies**

- `LOAN_FLOW_RATIO_INFO` — READ.

[↑ Back to API Index](#api-index)

<a id="get-stop-ratio-info"></a>

### get_stop_ratio_info

**Purpose:** Returns stop ratio info information for the supplied inputs.

**Signature**

```sql
FUNCTION get_stop_ratio_info(p_doc_no    VARCHAR2,
                               p_date      DATE DEFAULT glbl.getsysdate,
                               p_full_info varchar2 default 'N',
                               p_info_type varchar2 default 'INT')
    RETURN LOAN_STOP_RATE_TAB;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_date` | IN | Date |
| `p_full_info` | IN | Full info |
| `p_info_type` | IN | Info type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_STOP_RATIO_INFO`.

**Dependencies**

- `LOAN_STOP_RATIO_INFO` — READ.

[↑ Back to API Index](#api-index)

## Delinquency and status

<a id="get-ovd-trs-oper-type"></a>

### get_ovd_trs_oper_type

**Purpose:** Returns ovd trs oper type information for the supplied inputs.

**Signature**

```sql
function get_ovd_trs_oper_type(p_date               in date,
                                 p_acc_type_group     in varchar2,
                                 p_plan_date          in date,
                                 p_overdue_grace_days in number,
                                 p_balance            in number,
                                 p_overdue_min_amount in number,
                                 p_ovd_balance        in number,
                                 p_loan_end_date      in date,
                                 p_loan_status        in varchar2,
                                 P_OVERDUE_GRACE_DAYS_TYPE IN VARCHAR2,
                                 P_PLAN_TYPE               IN VARCHAR2,
                                 p_doc_no                  IN VARCHAR2 DEFAULT NULL)
    return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_date` | IN | Date |
| `p_acc_type_group` | IN | Acc type group |
| `p_plan_date` | IN | Plan date |
| `p_overdue_grace_days` | IN | Overdue grace days |
| `p_balance` | IN | Balance |
| `p_overdue_min_amount` | IN | Overdue min amount |
| `p_ovd_balance` | IN | Ovd balance |
| `p_loan_end_date` | IN | Loan end date |
| `p_loan_status` | IN | Loan status |
| `P_OVERDUE_GRACE_DAYS_TYPE` | IN | Overdue grace days type |
| `P_PLAN_TYPE` | IN | Plan type |
| `p_doc_no` | IN | Doc no |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_PAYMENT_PLAN`, `GAIA.LOAN_PAYMENT_PLAN`.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — READ.
- `GAIA.LOAN_PAYMENT_PLAN` — READ.

**Errors**

- `Overdue amount {` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-overdue-min-amount"></a>

### get_overdue_min_amount

**Purpose:** Returns overdue min amount information for the supplied inputs.

**Signature**

```sql
function get_overdue_min_amount(p_product_code in number,
                                  p_acc_type     in varchar2) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_product_code` | IN | Product code |
| `p_acc_type` | IN | Acc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `PKRD_TURKOD_PR`.

**Dependencies**

- `PKRD_TURKOD_PR` — READ.

**Errors**

- `Product code` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-overdue-grace-days"></a>

### get_overdue_grace_days

**Purpose:** Returns overdue grace days information for the supplied inputs.

**Signature**

```sql
function get_overdue_grace_days(p_product_code in number,
                                  p_acc_type     in varchar2) return number;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_product_code` | IN | Product code |
| `p_acc_type` | IN | Acc type |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `PKRD_TURKOD_PR`.

**Dependencies**

- `PKRD_TURKOD_PR` — READ.

**Errors**

- `Product code` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-ovd-date"></a>

### get_ovd_date

**Purpose:** Returns ovd date information for the supplied inputs.

**Signature**

```sql
Function get_ovd_date(p_doc_no   varchar2,
                        p_acc_type varchar2,
                        p_date     date default glbl.getsysdate, 
                        p_calc_mode varchar2 default 'DEFAULT'
                        ) return date;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_acc_type` | IN | Acc type |
| `p_date` | IN | Date |
| `p_calc_mode` | IN | Calc mode |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `GAIA.CS_ACCOUNT`, `LOAN_PAYMENT_PLAN` and other referenced sources.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `GAIA.CS_ACCOUNT` — READ.
- `LOAN_PAYMENT_PLAN` — READ.
- `CS_ACCOUNT` — READ.
- `LOAN_TRANCHE_API` — referenced package or interface.

**Errors**

- `p_calc_mode should be FOR_PEN_CALC - for penalty calculation, DEFAULT-for reporting` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-ovd-date-old"></a>

### get_ovd_date_old

**Purpose:** Returns ovd date old information for the supplied inputs.

**Signature**

```sql
Function get_ovd_date_old(p_doc_no   varchar2,
                        p_acc_type varchar2,
                        p_date     date default glbl.getsysdate,
                        p_calc_mode varchar2 default 'DEFAULT') return date;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_acc_type` | IN | Acc type |
| `p_date` | IN | Date |
| `p_calc_mode` | IN | Calc mode |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `LOAN_PAYMENT_PLAN`, `CS_ACCOUNT`.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `LOAN_PAYMENT_PLAN` — READ.
- `CS_ACCOUNT` — READ.
- `LOAN_TRANCHE_API` — referenced package or interface.

**Errors**

- `p_calc_mode should be FOR_PEN_CALC - for penalty calculation, DEFAULT-for reporting` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-loan-status-control"></a>

### do_loan_status_control

**Purpose:** Performs loan status control processing for the specified loan or scope.

**Signature**

```sql
procedure do_loan_status_control(p_branch_no   in number,
                                   p_customer_no in number,
                                   p_loan_acc    in number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_no` | IN | Branch no |
| `p_customer_no` | IN | Customer no |
| `p_loan_acc` | IN | Loan acc |

**Business Logic**

- Reads relevant data from `LOAN_PORTFOLIO_LITE`.

**Dependencies**

- `LOAN_PORTFOLIO_LITE` — READ.
- `GNI_MESSAGE` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="get-acc-type-by-status"></a>

### get_acc_type_by_status

**Purpose:** Returns acc type by status information for the supplied inputs.

**Signature**

```sql
function get_acc_type_by_status(p_acc_type         varchar2,
                                  p_to_loan_status   varchar2,
                                  p_from_loan_status varchar2 default 'NORM')
    return varchar2 result_cache;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_acc_type` | IN | Acc type |
| `p_to_loan_status` | IN | To loan status |
| `p_from_loan_status` | IN | From loan status |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_ACC_TYPE_MAPPING`.

**Dependencies**

- `LOAN_ACC_TYPE_MAPPING` — READ.

**Errors**

- `Can not find acc type [` (message fragment in source).
- `Something went wrong in [loan_acc_type_mapping], Acc Type [` (message fragment in source).

[↑ Back to API Index](#api-index)

## Limits, tranches and overdrafts

<a id="evaluate-limit-amount"></a>

### evaluate_limit_amount

**Purpose:** Evaluate limit amount for the supplied inputs.

**Signature**

```sql
procedure evaluate_limit_amount(p_min_id        number default 0,
                                  p_max_id        number default 999999999,
                                  p_doc_no        in varchar2,
                                  p_caller_tx_fid in number default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_min_id` | IN | Min id |
| `p_max_id` | IN | Max id |
| `p_doc_no` | IN | Doc no |
| `p_caller_tx_fid` | IN | Caller tx fid |

**Business Logic**

- Reads relevant data from `GAIA.LOAN_CATEGORY`, `GAIA.LOAN_OPERATION_HISTORY`, `CS_ACCOUNT` and other referenced sources.
- Invokes journal-entry processing as part of the operation.
- Records or updates loan operation history.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `GAIA.LOAN_CATEGORY` — READ.
- `GAIA.LOAN_OPERATION_HISTORY` — READ.
- `CS_ACCOUNT` — READ.
- `CARDS_ALL` — READ.
- `KRD_TEKLIF_DETAY` — READ.
- `GLBL_HESAP` — referenced package or interface.
- `LOAN_REPORT_API` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="do-create-tranche"></a>

### do_create_tranche

**Purpose:** Performs create tranche processing for the specified loan or scope.

**Signature**

```sql
procedure do_create_tranche(p_contract_no    varchar2,
                              p_tranche_type   varchar2 default null,
                              p_tracnhe_term   varchar2 default null,
                              p_tranche_amount number,
                              p_int_com_amount number default null,
                              p_trn_type       in varchar2,
                              p_tx_fid         in out number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_contract_no` | IN | Contract no |
| `p_tranche_type` | IN | Tranche type |
| `p_tracnhe_term` | IN | Tracnhe term |
| `p_tranche_amount` | IN | Tranche amount |
| `p_int_com_amount` | IN | Int com amount |
| `p_trn_type` | IN | Trn type |
| `p_tx_fid` | IN OUT | Tx fid |

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `GLBL_TRANSACTION`.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `GLBL_TRANSACTION` — READ.
- `APEX_KRD2204_0_API_P` — referenced package or interface.
- `KRD2204_0_API` — referenced package or interface.
- `LOAN_TRANCHE_API` — referenced package or interface.

**Errors**

- `In Creation this parameteres cant be p_contract_no or p_tranche_amount null!` (message fragment in source).
- `Does not find loan in [krd_teklif_detay] with contract_no [` (message fragment in source).
- `p_trn_type should be CREATE - for create, DELETE - for delete` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="create-overdrafts"></a>

### create_overdrafts

**Purpose:** Creates overdrafts records or associated operational data.

**Signature**

```sql
procedure create_overdrafts(p_customer in number default null,
                              p_min_id   in number default null,
                              p_max_id   in number default null, 
                              p_oper_type in varchar2 default 'CREATE_OVERDRAFT');
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_customer` | IN | Customer |
| `p_min_id` | IN | Min id |
| `p_max_id` | IN | Max id |
| `p_oper_type` | IN | Oper type |

**Business Logic**

- Modifies `KRD_TEKLIF_DETAY`, `CARDS_ALL`, `CS_ACCOUNT`, `TEMP_CARD_BALANCE`.
- Reads relevant data from `KRD_TEKLIF_DETAY`, `CARDS_ALL`, `CS_ACCOUNT` and other referenced sources.
- Invokes journal-entry processing as part of the operation.
- Records or updates loan operation history.
- Contains an explicit `COMMIT`; callers should review transaction ownership.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ, UPDATE.
- `CARDS_ALL` — READ, UPDATE.
- `CS_ACCOUNT` — READ, UPDATE.
- `EOD_PROGRAMS_EXCEPTION` — READ.
- `TEMP_CARD_BALANCE` — INSERT.
- `API_VISTA` — referenced package or interface.
- `GLBL_HESAP` — referenced package or interface.

**Errors**

- `p_oper_type should be CREATE_OVERDRAFT or CLOSE_LOAN` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="get-new-ov-cont-no"></a>

### get_new_ov_cont_no

**Purpose:** Returns new ov cont no information for the supplied inputs.

**Signature**

```sql
function get_new_ov_cont_no(p_branch_no in number,
                              p_cust_no   in number,
                              p_acc       in number) return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_branch_no` | IN | Branch no |
| `p_cust_no` | IN | Cust no |
| `p_acc` | IN | Acc |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `CS_ACCOUNT`, `KRD_TEKLIF_DETAY`.

**Dependencies**

- `CS_ACCOUNT` — READ.
- `KRD_TEKLIF_DETAY` — READ.

**Errors**

- `Musteri hesabi tapilmadi!` (message fragment in source).
- `Musteri melumatlarinda sehv var!` (message fragment in source).

[↑ Back to API Index](#api-index)

## History, metadata and reversals

<a id="clear-addtional-data"></a>

### clear_addtional_data

**Purpose:** Clear addtional data for the supplied inputs.

**Signature**

```sql
procedure clear_addtional_data(p_state varchar2 default 'CLEAR');
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_state` | IN | State |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

**Dependencies**

- `RUHA3H` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="add-additional-group"></a>

### add_additional_group

**Purpose:** Adds additional group information to the relevant loan processing context.

**Signature**

```sql
procedure add_additional_group(p_tag_name varchar2 default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tag_name` | IN | Tag name |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

**Dependencies**

- `APEX_JSON` — referenced package or interface.
- `RUHA3H` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="end-additional-group"></a>

### end_additional_group

**Purpose:** End additional group for the supplied inputs.

**Signature**

```sql
procedure end_additional_group;
```

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

**Dependencies**

- `RUHA3H` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="add-additional-info-1"></a>

### add_additional_info — overload 1

**Purpose:** Adds additional info information to the relevant loan processing context.

**Signature**

```sql
procedure add_additional_info(p_tag_name varchar2, p_value varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tag_name` | IN | Tag name |
| `p_value` | IN | Value |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

**Dependencies**

- `APEX_JSON` — referenced package or interface.
- `RUHA3H` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="add-additional-info-2"></a>

### add_additional_info — overload 2

**Purpose:** Adds additional info information to the relevant loan processing context.

**Signature**

```sql
procedure add_additional_info(p_tag_name varchar2, p_value date);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tag_name` | IN | Tag name |
| `p_value` | IN | Value |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

[↑ Back to API Index](#api-index)

<a id="add-column-update-1"></a>

### add_column_update — overload 1

**Purpose:** Adds column update information to the relevant loan processing context.

**Signature**

```sql
procedure add_column_update(p_tag_name   varchar2,
                              p_old_value  varchar2,
                              p_new_value  varchar2,
                              p_tranche_no number default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tag_name` | IN | Tag name |
| `p_old_value` | IN | Old value |
| `p_new_value` | IN | New value |
| `p_tranche_no` | IN | Tranche no |

**Business Logic**

- Reads relevant data from `LOAN_HISTORY_MAPPING`, `LOAN_TRANCHE_INFO`.

**Dependencies**

- `LOAN_HISTORY_MAPPING` — READ.
- `LOAN_TRANCHE_INFO` — READ.
- `RUHA3H` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="add-column-update-2"></a>

### add_column_update — overload 2

**Purpose:** Adds column update information to the relevant loan processing context.

**Signature**

```sql
procedure add_column_update(p_tag_name   varchar2,
                              p_old_value  date,
                              p_new_value  date,
                              p_tranche_no number default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tag_name` | IN | Tag name |
| `p_old_value` | IN | Old value |
| `p_new_value` | IN | New value |
| `p_tranche_no` | IN | Tranche no |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

[↑ Back to API Index](#api-index)

<a id="get-additional-info"></a>

### get_additional_info

**Purpose:** Returns additional info information for the supplied inputs.

**Signature**

```sql
function get_additional_info(p_Tx_fid number, p_tag_name varchar2)
    return varchar2;
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_Tx_fid` | IN | Tx fid |
| `p_tag_name` | IN | Tag name |

**Return:** See the declared return type; detailed result semantics are determined by the implementation.

**Business Logic**

- Reads relevant data from `LOAN_OPERATION_HISTORY`.

**Dependencies**

- `LOAN_OPERATION_HISTORY` — READ.
- `JSON_OBJECT_T` — referenced package or interface.
- `L_OBJ` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="finalize-addtional-process"></a>

### finalize_addtional_process

**Purpose:** Finalize addtional process for the supplied inputs.

**Signature**

```sql
procedure finalize_addtional_process(p_doc_no   varchar2,
                                       p_offer_id varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_offer_id` | IN | Offer id |

**Business Logic**

- Applies the specified operation using the supplied parameters and related package logic.

**Dependencies**

- `LOAN_TRANCHE_API` — referenced package or interface.

[↑ Back to API Index](#api-index)

<a id="reverse-update"></a>

### reverse_update

**Purpose:** Reverse update for the supplied inputs.

**Signature**

```sql
procedure reverse_update(p_tx_fid number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tx_fid` | IN | Tx fid |

**Business Logic**

- Reads relevant data from `LOAN_OPERATION_HISTORY`, `KRD_TEKLIF_DETAY`.

**Dependencies**

- `LOAN_OPERATION_HISTORY` — READ.
- `KRD_TEKLIF_DETAY` — READ.
- `JSON_OBJECT_T` — referenced package or interface.
- `L_LOG` — referenced package or interface.
- `L_OBJ` — referenced package or interface.
- `L_OLD` — referenced package or interface.
- `L_TRN` — referenced package or interface.

**Errors**

- `Can not get additional info in [loan_operation_history] with tx fid [` (message fragment in source).
- `Can not get find loan[` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="do-delete-operation"></a>

### do_delete_operation

**Purpose:** Performs delete operation processing for the specified loan or scope.

**Signature**

```sql
procedure do_delete_operation(p_tx_fid       number,
                                p_date_control varchar2 default 'Y',
                                p_plan_control varchar2 default 'Y');
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tx_fid` | IN | Tx fid |
| `p_date_control` | IN | Date control |
| `p_plan_control` | IN | Plan control |

**Business Logic**

- Modifies `GLBL_TRANSACTION`.
- Reads relevant data from `LOAN_OPERATION_HISTORY`, `GL_JOURNAL_LINES`.
- Records or updates loan operation history.

**Dependencies**

- `LOAN_OPERATION_HISTORY` — READ.
- `GL_JOURNAL_LINES` — READ.
- `GLBL_TRANSACTION` — UPDATE.
- `KRD_EOD` — referenced package or interface.
- `LOAN_TRANCHE_API` — referenced package or interface.
- `MM_ACCOUNTING#` — referenced package or interface.

**Errors**

- `Can not get additional info in [loan_operation_history] with tx fid [` (message fragment in source).
- `Not declared delete operation [` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="table-log-operation"></a>

### table_log_operation

**Purpose:** Table log operation for the supplied inputs.

**Signature**

```sql
procedure table_log_operation(p_doc_no     in varchar2,
                                p_table_name in varchar2,
                                p_tx_fid     in number,
                                p_oper_type  in varchar2);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_table_name` | IN | Table name |
| `p_tx_fid` | IN | Tx fid |
| `p_oper_type` | IN | Oper type |

**Business Logic**

- Modifies `LOAN_PAYMENT_PLAN`, `LOAN_PAYMENT_PLAN_LOG`, `LOAN_FLOW_RATIO_INFO`, `LOAN_FLOW_RATIO_INFO_LOG` and related records.
- Reads relevant data from `LOAN_PAYMENT_PLAN`, `LOAN_PAYMENT_PLAN_LOG`, `LOAN_FLOW_RATIO_INFO` and other referenced sources.

**Dependencies**

- `LOAN_PAYMENT_PLAN` — DELETE, INSERT, READ.
- `LOAN_PAYMENT_PLAN_LOG` — INSERT, READ.
- `LOAN_FLOW_RATIO_INFO` — DELETE, INSERT, READ.
- `LOAN_FLOW_RATIO_INFO_LOG` — INSERT, READ.
- `LOAN_STOP_RATIO_INFO` — DELETE, INSERT, READ.

**Errors**

- `p_tx_fid or p_document_no parameters cant be null!` (message fragment in source).
- `Oper type should be LOGGING-for logging or RESTORING-for restoring` (message fragment in source).
- `Table name should be [LOAN_PAYMENT_PLAN],[LOAN_FLOW_RATIO_INFO],[LOAN_STOP_RATIO_INFO],[LOAN_CATEGORY],[KRD_KOM_PLAN_DETAY]` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="create-loan-history"></a>

### create_loan_history

**Purpose:** Creates loan history records or associated operational data.

**Signature**

```sql
procedure create_loan_history(p_oper_type VARCHAR2 default null,
                                p_doc_no    VARCHAR2 default null,
                                p_trn_date  DATE default glbl.getsysdate,
                                p_tx_fid    NUMBER,
                                p_trn_type  varchar2,
                                p_add_info  add_info_tab default null);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_oper_type` | IN | Oper type |
| `p_doc_no` | IN | Doc no |
| `p_trn_date` | IN | Trn date |
| `p_tx_fid` | IN | Tx fid |
| `p_trn_type` | IN | Trn type |
| `p_add_info` | IN | Add info |

**Business Logic**

- Modifies `LOAN_OPERATION_HISTORY`.
- Reads relevant data from `LOAN_OPERATION_DESC`, `GLBL_TRANSACTION`, `GL_JOURNAL_LINES` and other referenced sources.
- Records or updates loan operation history.

**Dependencies**

- `LOAN_OPERATION_DESC` — READ.
- `GLBL_TRANSACTION` — READ.
- `GL_JOURNAL_LINES` — READ.
- `LOAN_OPERATION_HISTORY` — INSERT, READ, UPDATE.
- `TRN_BROKER` — referenced package or interface.

**Errors**

- `p_app_oper_code not found in loan_operation_desc table!` (message fragment in source).
- `Transaction with tx_fid:` (message fragment in source).
- `You need delete this operation(s) [` (message fragment in source).
- `p_trn_type must be I-insert, U-update, D-delete` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="update-loan-history"></a>

### update_loan_history

**Purpose:** Updates loan history information for the specified context.

**Signature**

```sql
procedure update_loan_history(p_tx_fid number);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_tx_fid` | IN | Tx fid |

**Business Logic**

- Modifies `LOAN_OPERATION_HISTORY`.
- Reads relevant data from `LOAN_OPERATION_HISTORY`, `GL_JOURNAL_LINES`, `CS_ACCOUNT` and other referenced sources.
- Records or updates loan operation history.

**Dependencies**

- `LOAN_OPERATION_HISTORY` — MERGE, READ.
- `GL_JOURNAL_LINES` — READ.
- `CS_ACCOUNT` — READ.
- `LOAN_OPERATION_DESC` — READ.
- `LOAN_TRANCHE_API` — referenced package or interface.

**Errors**

- `[p_tx_fid] is null at [loan_api.update_loan_history]` (message fragment in source).
- `Can not find information in [loan_operation_history] with tx fid [` (message fragment in source).
- `Find duplicate information in [loan_operation_history] with tx fid [` (message fragment in source).

[↑ Back to API Index](#api-index)

<a id="init-global-variables"></a>

### init_global_variables

**Purpose:** Init global variables for the supplied inputs.

**Signature**

```sql
Procedure init_global_variables(p_doc_no varchar2,
                                  p_reset  boolean default false);
```

**Parameters**

| Parameter | Direction | Description |
|---|---|---|
| `p_doc_no` | IN | Doc no |
| `p_reset` | IN | Reset |

**Business Logic**

- Reads relevant data from `KRD_TEKLIF_DETAY`, `KRD_TEKLIF`, `KRD_TESIS` and other referenced sources.

**Dependencies**

- `KRD_TEKLIF_DETAY` — READ.
- `KRD_TEKLIF` — READ.
- `KRD_TESIS` — READ.
- `KRD_ODEME_PLAN` — READ.

**Errors**

- `[krd_teklif_detay] is invalid` (message fragment in source).
- `[krd_teklif] is invalid` (message fragment in source).
- `[krd_tesis] is invalid` (message fragment in source).
- `[krd_odeme_plan] is invalid` (message fragment in source).

[↑ Back to API Index](#api-index)
