# psoc_ble
Information I've collected about Cypress PSoC BLE

## Events
| Category | Int Val | Event Name |
| --- | --- | --- |
| Generic | 0x0000 | [CYBLE_EVT_HOST_INVALID](#cyble_evt_host_invalid) |
| Generic | 0x0001 | [CYBLE_EVT_STACK_ON](#cyble_evt_stack_on) |
| Generic | 0x0002 | [CYBLE_EVT_TIMEOUT](#cyble_evt_timeout) |
| Generic | 0x0003 | [CYBLE_EVT_HARDWARE_ERROR](#cyble_evt_hardware_error) |
| Generic | 0x0004 | [CYBLE_EVT_HCI_STATUS](#cyble_evt_hci_status) |
| Generic | 0x0005 | [CYBLE_EVT_STACK_BUSY_STATUS](#cyble_evt_stack_busy_status) |
| Generic | 0x0006 | [CYBLE_EVT_MEMORY_REQUEST](#cyble_evt_memory_request) |
| GAP | 0x0020 | [CYBLE_EVT_GAPC_SCAN_PROGRESS_RESULT](#cyble_evt_gapc_scan_progress_result) |
| GAP | 0x0021 | [CYBLE_EVT_GAP_AUTH_REQ](#cyble_evt_gap_auth_req) |
| GAP | 0x0022 | [CYBLE_EVT_GAP_PASSKEY_ENTRY_REQUEST](#cyble_evt_gap_passkey_entry_request) |
| GAP | 0x0023 | [CYBLE_EVT_GAP_PASSKEY_DISPLAY_REQUEST](#cyble_evt_gap_passkey_display_request) |
| GAP | 0x0024 | [CYBLE_EVT_GAP_AUTH_COMPLETE](#cyble_evt_gap_auth_complete) |
| GAP | 0x0025 | [CYBLE_EVT_GAP_AUTH_FAILED](#cyble_evt_gap_auth_failed) |
| GAP | 0x0026 | [CYBLE_EVT_GAPP_ADVERTISEMENT_START_STOP](#cyble_evt_gapp_advertisement_start_stop) |
| GAP | 0x0027 | [CYBLE_EVT_GAP_DEVICE_CONNECTED](#cyble_evt_gap_device_connected) |
| GAP | 0x0028 | [CYBLE_EVT_GAP_DEVICE_DISCONNECTED](#cyble_evt_gap_device_disconnected) |
| GAP | 0x0029 | [CYBLE_EVT_GAP_ENCRYPT_CHANGE](#cyble_evt_gap_encrypt_change) |
| GAP | 0x002A | [CYBLE_EVT_GAP_CONNECTION_UPDATE_COMPLETE](#cyble_evt_gap_connection_update_complete) |
| GAP | 0x002B | [CYBLE_EVT_GAPC_SCAN_START_STOP](#cyble_evt_gapc_scan_start_stop) |
| GAP | 0x002C | [CYBLE_EVT_GAP_KEYINFO_EXCHNGE_CMPLT](#cyble_evt_gap_keyinfo_exchnge_cmplt) |
| GAP | 0x002D | [CYBLE_EVT_GAP_NUMERIC_COMPARISON_REQUEST](#cyble_evt_gap_numeric_comparison_request) |
| GAP | 0x002E | [CYBLE_EVT_GAP_KEYPRESS_NOTIFICATION](#cyble_evt_gap_keypress_notification) |
| GAP | 0x002F | [CYBLE_EVT_GAP_OOB_GENERATED_NOTIFICATION](#cyble_evt_gap_oob_generated_notification) |
| GAP | 0x0030 | [CYBLE_EVT_GAP_DATA_LENGTH_CHANGE](#cyble_evt_gap_data_length_change) |
| GAP | 0x0031 | [CYBLE_EVT_GAP_ENHANCE_CONN_COMPLETE](#cyble_evt_gap_enhance_conn_complete) |
| GAP | 0x0032 | [CYBLE_EVT_GAPC_DIRECT_ADV_REPORT](#cyble_evt_gapc_direct_adv_report) |
| GAP | 0x0033 | [CYBLE_EVT_GAP_SMP_NEGOTIATED_AUTH_INFO](#cyble_evt_gap_smp_negotiated_auth_info) |
| GATT | 0x0040 | [CYBLE_EVT_GATTC_ERROR_RSP](#cyble_evt_gattc_error_rsp) |
| GATT | 0x0041 | [CYBLE_EVT_GATT_CONNECT_IND](#cyble_evt_gatt_connect_ind) |
| GATT | 0x0042 | [CYBLE_EVT_GATT_DISCONNECT_IND](#cyble_evt_gatt_disconnect_ind) |
| GATT | 0x0043 | [CYBLE_EVT_GATTS_XCNHG_MTU_REQ](#cyble_evt_gatts_xcnhg_mtu_req) |
| GATT | 0x0044 | [CYBLE_EVT_GATTC_XCHNG_MTU_RSP](#cyble_evt_gattc_xchng_mtu_rsp) |
| GATT | 0x0045 | [CYBLE_EVT_GATTC_READ_BY_GROUP_TYPE_RSP](#cyble_evt_gattc_read_by_group_type_rsp) |
| GATT | 0x0046 | [CYBLE_EVT_GATTC_READ_BY_TYPE_RSP](#cyble_evt_gattc_read_by_type_rsp) |
| GATT | 0x0047 | [CYBLE_EVT_GATTC_FIND_INFO_RSP](#cyble_evt_gattc_find_info_rsp) |
| GATT | 0x0048 | [CYBLE_EVT_GATTC_FIND_BY_TYPE_VALUE_RSP](#cyble_evt_gattc_find_by_type_value_rsp) |
| GATT | 0x0049 | [CYBLE_EVT_GATTC_READ_RSP](#cyble_evt_gattc_read_rsp) |
| GATT | 0x004A | [CYBLE_EVT_GATTC_READ_BLOB_RSP](#cyble_evt_gattc_read_blob_rsp) |
| GATT | 0x004B | [CYBLE_EVT_GATTC_READ_MULTI_RSP](#cyble_evt_gattc_read_multi_rsp) |
| GATT | 0x004C | [CYBLE_EVT_GATTS_WRITE_REQ](#cyble_evt_gatts_write_req) |
| GATT | 0x004D | [CYBLE_EVT_GATTC_WRITE_RSP](#cyble_evt_gattc_write_rsp) |
| GATT | 0x004E | [CYBLE_EVT_GATTS_WRITE_CMD_REQ](#cyble_evt_gatts_write_cmd_req) |
| GATT | 0x004F | [CYBLE_EVT_GATTS_PREP_WRITE_REQ](#cyble_evt_gatts_prep_write_req) |
| GATT | 0x0050 | [CYBLE_EVT_GATTS_EXEC_WRITE_REQ](#cyble_evt_gatts_exec_write_req) |
| GATT | 0x0051 | [CYBLE_EVT_GATTC_EXEC_WRITE_RSP](#cyble_evt_gattc_exec_write_rsp) |
| GATT | 0x0052 | [CYBLE_EVT_GATTC_HANDLE_VALUE_NTF](#cyble_evt_gattc_handle_value_ntf) |
| GATT | 0x0053 | [CYBLE_EVT_GATTC_HANDLE_VALUE_IND](#cyble_evt_gattc_handle_value_ind) |
| GATT | 0x0054 | [CYBLE_EVT_GATTS_HANDLE_VALUE_CNF](#cyble_evt_gatts_handle_value_cnf) |
| GATT | 0x0055 | [CYBLE_EVT_GATTS_DATA_SIGNED_CMD_REQ](#cyble_evt_gatts_data_signed_cmd_req) |
| GATT | 0x0056 | [CYBLE_EVT_GATTC_STOP_CMD_COMPLETE](#cyble_evt_gattc_stop_cmd_complete) |
| GATT | 0x0057 | [CYBLE_EVT_GATTS_READ_CHAR_VAL_ACCESS_REQ](#cyble_evt_gatts_read_char_val_access_req) |
| GATT | 0x0058 | [CYBLE_EVT_GATTC_LONG_PROCEDURE_END](#cyble_evt_gattc_long_procedure_end) |
| L2CAP | 0x0070 | [CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_REQ](#cyble_evt_l2cap_conn_param_update_req) |
| L2CAP | 0x0071 | [CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_RSP](#cyble_evt_l2cap_conn_param_update_rsp) |
| L2CAP | 0x0072 | [CYBLE_EVT_L2CAP_COMMAND_REJ](#cyble_evt_l2cap_command_rej) |
| L2CAP | 0x0073 | [CYBLE_EVT_L2CAP_CBFC_CONN_IND](#cyble_evt_l2cap_cbfc_conn_ind) |
| L2CAP | 0x0074 | [CYBLE_EVT_L2CAP_CBFC_CONN_CNF](#cyble_evt_l2cap_cbfc_conn_cnf) |
| L2CAP | 0x0075 | [CYBLE_EVT_L2CAP_CBFC_DISCONN_IND](#cyble_evt_l2cap_cbfc_disconn_ind) |
| L2CAP | 0x0076 | [CYBLE_EVT_L2CAP_CBFC_DISCONN_CNF](#cyble_evt_l2cap_cbfc_disconn_cnf) |
| L2CAP | 0x0077 | [CYBLE_EVT_L2CAP_CBFC_DATA_READ](#cyble_evt_l2cap_cbfc_data_read) |
| L2CAP | 0x0078 | [CYBLE_EVT_L2CAP_CBFC_RX_CREDIT_IND](#cyble_evt_l2cap_cbfc_rx_credit_ind) |
| L2CAP | 0x0079 | [CYBLE_EVT_L2CAP_CBFC_TX_CREDIT_IND](#cyble_evt_l2cap_cbfc_tx_credit_ind) |
| L2CAP | 0x007A | [CYBLE_EVT_L2CAP_CBFC_DATA_WRITE_IND](#cyble_evt_l2cap_cbfc_data_write_ind) |
| Host Qualification | 0x0080 | [CYBLE_EVT_QUAL_SMP_PAIRING_REQ_RSP](#cyble_evt_qual_smp_pairing_req_rsp) |
| Host Qualification | 0x0081 | [CYBLE_EVT_QUAL_SMP_LOCAL_PUBLIC_KEY](#cyble_evt_qual_smp_local_public_key) |
| Host Qualification | 0x0082 | [CYBLE_EVT_QUAL_SMP_PAIRING_FAILED_CMD](#cyble_evt_qual_smp_pairing_failed_cmd) |
| Future Use | 0x00FA | [CYBLE_EVT_PENDING_FLASH_WRITE](#cyble_evt_pending_flash_write) |
| Future Use | 0x00FB | [CYBLE_EVT_LE_PING_AUTH_TIMEOUT](#cyble_evt_le_ping_auth_timeout) |
| Generic | 0x00FF | [CYBLE_EVT_MAX](#cyble_evt_max) |

### CYBLE_EVT_HOST_INVALID
This event is triggered by BLE stack when stack is in a bad state, restarting stack is the only way to get out
of the state

### CYBLE_EVT_STACK_ON
This event is received when BLE stack is initialized and turned ON by invoking CyBle_StackInit () function.

### CYBLE_EVT_TIMEOUT
This event is received when there is a timeout and application needs to handle the event. Timeout reason is
defined by CYBLE_TO_REASON_CODE_T.

### CYBLE_EVT_HARDWARE_ERROR
This event indicates that some internal hardware error has occurred. Reset of the hardware may be required.

### CYBLE_EVT_HCI_STATUS
This event is triggered by 'Host Stack' if 'Controller' responds with an error code for any HCI command.
Event parameter returned will be an HCI error code as defined in Bluetooth 4.1 core specification, Volume 2,
Part D, section 1.3. This event will be received only if there is an error.

### CYBLE_EVT_STACK_BUSY_STATUS
This event is triggered by host stack if BLE stack is busy or not. 
Event Parameter corresponding to this event will indicate the state of BLE stack's internal protocol buffers
for the application to safely initiate data transactions (GATT, GAP Security, and L2CAP transactions)
with the peer BLE device.
Event parameter is of type uint8.
* CYBLE_STACK_STATE_BUSY (0x01) = CYBLE_STACK_STATE_BUSY indicates application that BLE stack's internal buffers
    are about to be filled, and the remaining buffers are required to respond peer BLE device
    After this event, application shall not initiate (GATT, GAP Security and L2CAP data transactions). 
    However application shall respond to peer initiated transactions to prevent BLE protocol timeouts
    to occur.
    Application initiated data transactions can be resumed after CYBLE_EVT_STACK_BUSY_STATUS
    event with parameter 'CYBLE_STACK_STATE_FREE' is received.

* CYBLE_STACK_STATE_FREE (0x00) = CYBLE_STACK_STATE_FREE indicates application that pending transactions are completed
*                   and sufficient buffers are available to process application initiated transactions.
*                   The 'CYBLE_EVT_STACK_BUSY_STATUS' event with 'CYBLE_STACK_STATE_FREE' is indicated to 
*                   application if BLE Stack's internal buffer state has transitioned from 'CYBLE_STACK_STATE_BUSY'
*                   to 'CYBLE_STACK_STATE_FREE'.
*
To increase BLE stack's internal buffers count and achieve better throughput for attribute MTU greater then 32, 
use MaxAttrNoOfBuffer parameter in the Expression view of the Advanced tab.    