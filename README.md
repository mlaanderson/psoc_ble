# psoc_ble
Information I've collected about Cypress PSoC BLE

* [Events](#events)
* [Types](#types)

## Types

### CYBLE_TO_REASON_CODE_T
BLE stack timeout. This is received with [CYBLE_EVT_TIMEOUT](#cyble_evt_timeout) event.

It is application's responsibility to disconnect or keep the channel on depends on type of timeouts.
i.e. GATT procedure timeout: Application may choose to disconnect.

#### Enum
##### CYBLE_GAP_ADV_MODE_TO = 1
Advertisement time set by application has expired

##### CYBLE_GAP_SCAN_TO = 2
Scan time set by application has expired

##### CYBLE_GATT_RSP_TO = 3
GATT procedure timeout

##### CYBLE_GENERIC_TO = 4
Generic timeout

### CYBLE_GAP_AUTH_FAILED_REASON_T
Authentication Failed Error Codes

#### enum

##### CYBLE_GAP_AUTH_ERROR_NONE  = 0
No Error

##### CYBLE_GAP_AUTH_ERROR_PASSKEY_ENTRY_FAILED = 1
User input of passkey failed, for example, the user cancelled the operation 

##### CYBLE_GAP_AUTH_ERROR_OOB_DATA_NOT_AVAILABLE = 2
Out Of Band data is not available, applicable if NFC is supported 

##### CYBLE_GAP_AUTH_ERROR_AUTHENTICATION_REQ_NOT_MET = 3
Pairing procedure cannot be performed as authentication
requirements cannot be met due to IO capabilities of one or both devices. 

##### CYBLE_GAP_AUTH_ERROR_CONFIRM_VALUE_NOT_MATCH = 4
Confirm value does not match the calculated compare value  

##### CYBLE_GAP_AUTH_ERROR_PAIRING_NOT_SUPPORTED = 5
Pairing is not supported by the device 

##### CYBLE_GAP_AUTH_ERROR_INSUFFICIENT_ENCRYPTION_KEY_SIZE = 6
Insufficient key size for the security requirements of this device 

##### CYBLE_GAP_AUTH_ERROR_COMMAND_NOT_SUPPORTED = 7
command received is not supported 

##### CYBLE_GAP_AUTH_ERROR_UNSPECIFIED_REASON = 8
Pairing failed due to an unspecified reason 

##### CYBLE_GAP_AUTH_ERROR_REPEATED_ATTEMPTS = 9
Pairing or authentication procedure is disallowed because too little time
has elapsed since last pairing request or security request. 

##### CYBLE_GAP_AUTH_ERROR_INVALID_PARAMETERS = 10
Invalid Parameters in Request - Invalid Command length and Parameter value outside range 

##### CYBLE_GAP_AUTH_ERROR_DHKEY_CHECK_FAILED = 11
Indicates to the remote device that the DHKey Check value received doesn't
match the one calculated by the local device 

##### CYBLE_GAP_AUTH_ERROR_NUMERIC_COMPARISON_FAILED = 12
Indicates that the confirm values in the numeric comparison protocol
do not match 

##### CYBLE_GAP_AUTH_ERROR_BR_EDR_PAIRING_IN_PROGRESS = 13
Indicates that the pairing over the LE transport failed due to a Pairing
Request sent over the BR/EDR transport is in process. 

##### CYBLE_GAP_AUTH_ERROR_CROSS_TRANSPORT_KEY_GEN_DER_NOT_ALLOWED = 14
Indicates that the BR/EDR Link Key generated on the BR/EDR transport cannot
be used to derive and distribute keys for LE transport 

##### CYBLE_GAP_AUTH_ERROR_AUTHENTICATION_TIMEOUT = 21
Authentication process timeout, if pairing timeout happens for first time, 
application can choose to re-initiate the pairing procedure. If timeout occurs again, 
app may choose to disconnect peer device. 

##### CYBLE_GAP_AUTH_ERROR_LINK_DISCONNECTED = 24
Link disconnected 

## Events
| Category | Int Val | Event Name |
| --- | --- | --- |
| [Generic](#generic-events) | [0x0000](#cyble_evt_host_invalid) | [CYBLE_EVT_HOST_INVALID](#cyble_evt_host_invalid) |
| [Generic](#generic-events) | [0x0001](#cyble_evt_stack_on) | [CYBLE_EVT_STACK_ON](#cyble_evt_stack_on) |
| [Generic](#generic-events) | [0x0002](#cyble_evt_timeout) | [CYBLE_EVT_TIMEOUT](#cyble_evt_timeout) |
| [Generic](#generic-events) | [0x0003](#cyble_evt_hardware_error) | [CYBLE_EVT_HARDWARE_ERROR](#cyble_evt_hardware_error) |
| [Generic](#generic-events) | [0x0004](#cyble_evt_hci_status) | [CYBLE_EVT_HCI_STATUS](#cyble_evt_hci_status) |
| [Generic](#generic-events) | [0x0005](#cyble_evt_stack_busy_status) | [CYBLE_EVT_STACK_BUSY_STATUS](#cyble_evt_stack_busy_status) |
| [Generic](#generic-events) | [0x0006](#cyble_evt_memory_request) | [CYBLE_EVT_MEMORY_REQUEST](#cyble_evt_memory_request) |
| [GAP](#gap-events) | [0x0020](#cyble_evt_gapc_scan_progress_result) | [CYBLE_EVT_GAPC_SCAN_PROGRESS_RESULT](#cyble_evt_gapc_scan_progress_result) |
| [GAP](#gap-events) | [0x0021](#cyble_evt_gap_auth_req) | [CYBLE_EVT_GAP_AUTH_REQ](#cyble_evt_gap_auth_req) |
| [GAP](#gap-events) | [0x0022](#cyble_evt_gap_passkey_entry_request) | [CYBLE_EVT_GAP_PASSKEY_ENTRY_REQUEST](#cyble_evt_gap_passkey_entry_request) |
| [GAP](#gap-events) | [0x0023](#cyble_evt_gap_passkey_display_request) | [CYBLE_EVT_GAP_PASSKEY_DISPLAY_REQUEST](#cyble_evt_gap_passkey_display_request) |
| [GAP](#gap-events) | [0x0024](#cyble_evt_gap_auth_complete) | [CYBLE_EVT_GAP_AUTH_COMPLETE](#cyble_evt_gap_auth_complete) |
| [GAP](#gap-events) | [0x0025](#cyble_evt_gap_auth_failed) | [CYBLE_EVT_GAP_AUTH_FAILED](#cyble_evt_gap_auth_failed) |
| [GAP](#gap-events) | [0x0026](#cyble_evt_gapp_advertisement_start_stop) | [CYBLE_EVT_GAPP_ADVERTISEMENT_START_STOP](#cyble_evt_gapp_advertisement_start_stop) |
| [GAP](#gap-events) | [0x0027](#cyble_evt_gap_device_connected) | [CYBLE_EVT_GAP_DEVICE_CONNECTED](#cyble_evt_gap_device_connected) |
| [GAP](#gap-events) | [0x0028](#cyble_evt_gap_device_disconnected) | [CYBLE_EVT_GAP_DEVICE_DISCONNECTED](#cyble_evt_gap_device_disconnected) |
| [GAP](#gap-events) | [0x0029](#cyble_evt_gap_encrypt_change) | [CYBLE_EVT_GAP_ENCRYPT_CHANGE](#cyble_evt_gap_encrypt_change) |
| [GAP](#gap-events) | [0x002A](#cyble_evt_gap_connection_update_complete) | [CYBLE_EVT_GAP_CONNECTION_UPDATE_COMPLETE](#cyble_evt_gap_connection_update_complete) |
| [GAP](#gap-events) | [0x002B](#cyble_evt_gapc_scan_start_stop) | [CYBLE_EVT_GAPC_SCAN_START_STOP](#cyble_evt_gapc_scan_start_stop) |
| [GAP](#gap-events) | [0x002C](#cyble_evt_gap_keyinfo_exchnge_cmplt) | [CYBLE_EVT_GAP_KEYINFO_EXCHNGE_CMPLT](#cyble_evt_gap_keyinfo_exchnge_cmplt) |
| [GAP](#gap-events) | [0x002D](#cyble_evt_gap_numeric_comparison_request) | [CYBLE_EVT_GAP_NUMERIC_COMPARISON_REQUEST](#cyble_evt_gap_numeric_comparison_request) |
| [GAP](#gap-events) | [0x002E](#cyble_evt_gap_keypress_notification) | [CYBLE_EVT_GAP_KEYPRESS_NOTIFICATION](#cyble_evt_gap_keypress_notification) |
| [GAP](#gap-events) | [0x002F](#cyble_evt_gap_oob_generated_notification) | [CYBLE_EVT_GAP_OOB_GENERATED_NOTIFICATION](#cyble_evt_gap_oob_generated_notification) |
| [GAP](#gap-events) | [0x0030](#cyble_evt_gap_data_length_change) | [CYBLE_EVT_GAP_DATA_LENGTH_CHANGE](#cyble_evt_gap_data_length_change) |
| [GAP](#gap-events) | [0x0031](#cyble_evt_gap_enhance_conn_complete) | [CYBLE_EVT_GAP_ENHANCE_CONN_COMPLETE](#cyble_evt_gap_enhance_conn_complete) |
| [GAP](#gap-events) | [0x0032](#cyble_evt_gapc_direct_adv_report) | [CYBLE_EVT_GAPC_DIRECT_ADV_REPORT](#cyble_evt_gapc_direct_adv_report) |
| [GAP](#gap-events) | [0x0033](#cyble_evt_gap_smp_negotiated_auth_info) | [CYBLE_EVT_GAP_SMP_NEGOTIATED_AUTH_INFO](#cyble_evt_gap_smp_negotiated_auth_info) |
| [GATT](#gatt-events) | [0x0040](#cyble_evt_gattc_error_rsp) | [CYBLE_EVT_GATTC_ERROR_RSP](#cyble_evt_gattc_error_rsp) |
| [GATT](#gatt-events) | [0x0041](#cyble_evt_gatt_connect_ind) | [CYBLE_EVT_GATT_CONNECT_IND](#cyble_evt_gatt_connect_ind) |
| [GATT](#gatt-events) | [0x0042](#cyble_evt_gatt_disconnect_ind) | [CYBLE_EVT_GATT_DISCONNECT_IND](#cyble_evt_gatt_disconnect_ind) |
| [GATT](#gatt-events) | [0x0043](#cyble_evt_gatts_xcnhg_mtu_req) | [CYBLE_EVT_GATTS_XCNHG_MTU_REQ](#cyble_evt_gatts_xcnhg_mtu_req) |
| [GATT](#gatt-events) | [0x0044](#cyble_evt_gattc_xchng_mtu_rsp) | [CYBLE_EVT_GATTC_XCHNG_MTU_RSP](#cyble_evt_gattc_xchng_mtu_rsp) |
| [GATT](#gatt-events) | [0x0045](#cyble_evt_gattc_read_by_group_type_rsp) | [CYBLE_EVT_GATTC_READ_BY_GROUP_TYPE_RSP](#cyble_evt_gattc_read_by_group_type_rsp) |
| [GATT](#gatt-events) | [0x0046](#cyble_evt_gattc_read_by_type_rsp) | [CYBLE_EVT_GATTC_READ_BY_TYPE_RSP](#cyble_evt_gattc_read_by_type_rsp) |
| [GATT](#gatt-events) | [0x0047](#cyble_evt_gattc_find_info_rsp) | [CYBLE_EVT_GATTC_FIND_INFO_RSP](#cyble_evt_gattc_find_info_rsp) |
| [GATT](#gatt-events) | [0x0048](#cyble_evt_gattc_find_by_type_value_rsp) | [CYBLE_EVT_GATTC_FIND_BY_TYPE_VALUE_RSP](#cyble_evt_gattc_find_by_type_value_rsp) |
| [GATT](#gatt-events) | [0x0049](#cyble_evt_gattc_read_rsp) | [CYBLE_EVT_GATTC_READ_RSP](#cyble_evt_gattc_read_rsp) |
| [GATT](#gatt-events) | [0x004A](#cyble_evt_gattc_read_blob_rsp) | [CYBLE_EVT_GATTC_READ_BLOB_RSP](#cyble_evt_gattc_read_blob_rsp) |
| [GATT](#gatt-events) | [0x004B](#cyble_evt_gattc_read_multi_rsp) | [CYBLE_EVT_GATTC_READ_MULTI_RSP](#cyble_evt_gattc_read_multi_rsp) |
| [GATT](#gatt-events) | [0x004C](#cyble_evt_gatts_write_req) | [CYBLE_EVT_GATTS_WRITE_REQ](#cyble_evt_gatts_write_req) |
| [GATT](#gatt-events) | [0x004D](#cyble_evt_gattc_write_rsp) | [CYBLE_EVT_GATTC_WRITE_RSP](#cyble_evt_gattc_write_rsp) |
| [GATT](#gatt-events) | [0x004E](#cyble_evt_gatts_write_cmd_req) | [CYBLE_EVT_GATTS_WRITE_CMD_REQ](#cyble_evt_gatts_write_cmd_req) |
| [GATT](#gatt-events) | [0x004F](#cyble_evt_gatts_prep_write_req) | [CYBLE_EVT_GATTS_PREP_WRITE_REQ](#cyble_evt_gatts_prep_write_req) |
| [GATT](#gatt-events) | [0x0050](#cyble_evt_gatts_exec_write_req) | [CYBLE_EVT_GATTS_EXEC_WRITE_REQ](#cyble_evt_gatts_exec_write_req) |
| [GATT](#gatt-events) | [0x0051](#cyble_evt_gattc_exec_write_rsp) | [CYBLE_EVT_GATTC_EXEC_WRITE_RSP](#cyble_evt_gattc_exec_write_rsp) |
| [GATT](#gatt-events) | [0x0052](#cyble_evt_gattc_handle_value_ntf) | [CYBLE_EVT_GATTC_HANDLE_VALUE_NTF](#cyble_evt_gattc_handle_value_ntf) |
| [GATT](#gatt-events) | [0x0053](#cyble_evt_gattc_handle_value_ind) | [CYBLE_EVT_GATTC_HANDLE_VALUE_IND](#cyble_evt_gattc_handle_value_ind) |
| [GATT](#gatt-events) | [0x0054](#cyble_evt_gatts_handle_value_cnf) | [CYBLE_EVT_GATTS_HANDLE_VALUE_CNF](#cyble_evt_gatts_handle_value_cnf) |
| [GATT](#gatt-events) | [0x0055](#cyble_evt_gatts_data_signed_cmd_req) | [CYBLE_EVT_GATTS_DATA_SIGNED_CMD_REQ](#cyble_evt_gatts_data_signed_cmd_req) |
| [GATT](#gatt-events) | [0x0056](#cyble_evt_gattc_stop_cmd_complete) | [CYBLE_EVT_GATTC_STOP_CMD_COMPLETE](#cyble_evt_gattc_stop_cmd_complete) |
| [GATT](#gatt-events) | [0x0057](#cyble_evt_gatts_read_char_val_access_req) | [CYBLE_EVT_GATTS_READ_CHAR_VAL_ACCESS_REQ](#cyble_evt_gatts_read_char_val_access_req) |
| [GATT](#gatt-events) | [0x0058](#cyble_evt_gattc_long_procedure_end) | [CYBLE_EVT_GATTC_LONG_PROCEDURE_END](#cyble_evt_gattc_long_procedure_end) |
| [L2CAP](#l2cap-events) | [0x0070](#cyble_evt_l2cap_conn_param_update_req) | [CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_REQ](#cyble_evt_l2cap_conn_param_update_req) |
| [L2CAP](#l2cap-events) | [0x0071](#cyble_evt_l2cap_conn_param_update_rsp) | [CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_RSP](#cyble_evt_l2cap_conn_param_update_rsp) |
| [L2CAP](#l2cap-events) | [0x0072](#cyble_evt_l2cap_command_rej) | [CYBLE_EVT_L2CAP_COMMAND_REJ](#cyble_evt_l2cap_command_rej) |
| [L2CAP](#l2cap-events) | [0x0073](#cyble_evt_l2cap_cbfc_conn_ind) | [CYBLE_EVT_L2CAP_CBFC_CONN_IND](#cyble_evt_l2cap_cbfc_conn_ind) |
| [L2CAP](#l2cap-events) | [0x0074](#cyble_evt_l2cap_cbfc_conn_cnf) | [CYBLE_EVT_L2CAP_CBFC_CONN_CNF](#cyble_evt_l2cap_cbfc_conn_cnf) |
| [L2CAP](#l2cap-events) | [0x0075](#cyble_evt_l2cap_cbfc_disconn_ind) | [CYBLE_EVT_L2CAP_CBFC_DISCONN_IND](#cyble_evt_l2cap_cbfc_disconn_ind) |
| [L2CAP](#l2cap-events) | [0x0076](#cyble_evt_l2cap_cbfc_disconn_cnf) | [CYBLE_EVT_L2CAP_CBFC_DISCONN_CNF](#cyble_evt_l2cap_cbfc_disconn_cnf) |
| [L2CAP](#l2cap-events) | [0x0077](#cyble_evt_l2cap_cbfc_data_read) | [CYBLE_EVT_L2CAP_CBFC_DATA_READ](#cyble_evt_l2cap_cbfc_data_read) |
| [L2CAP](#l2cap-events) | [0x0078](#cyble_evt_l2cap_cbfc_rx_credit_ind) | [CYBLE_EVT_L2CAP_CBFC_RX_CREDIT_IND](#cyble_evt_l2cap_cbfc_rx_credit_ind) |
| [L2CAP](#l2cap-events) | [0x0079](#cyble_evt_l2cap_cbfc_tx_credit_ind) | [CYBLE_EVT_L2CAP_CBFC_TX_CREDIT_IND](#cyble_evt_l2cap_cbfc_tx_credit_ind) |
| [L2CAP](#l2cap-events) | [0x007A](#cyble_evt_l2cap_cbfc_data_write_ind) | [CYBLE_EVT_L2CAP_CBFC_DATA_WRITE_IND](#cyble_evt_l2cap_cbfc_data_write_ind) |
| [Host Qualification](#host-qualification-events) | [0x0080](#cyble_evt_qual_smp_pairing_req_rsp) | [CYBLE_EVT_QUAL_SMP_PAIRING_REQ_RSP](#cyble_evt_qual_smp_pairing_req_rsp) |
| [Host Qualification](#host-qualification-events) | [0x0081](#cyble_evt_qual_smp_local_public_key) | [CYBLE_EVT_QUAL_SMP_LOCAL_PUBLIC_KEY](#cyble_evt_qual_smp_local_public_key) |
| [Host Qualification](#host-qualification-events) | [0x0082](#cyble_evt_qual_smp_pairing_failed_cmd) | [CYBLE_EVT_QUAL_SMP_PAIRING_FAILED_CMD](#cyble_evt_qual_smp_pairing_failed_cmd) |
| [Future Use](#future-use-events) | [0x00FA](#cyble_evt_pending_flash_write) | [CYBLE_EVT_PENDING_FLASH_WRITE](#cyble_evt_pending_flash_write) |
| [Future Use](#future-use-events) | [0x00FB](#cyble_evt_le_ping_auth_timeout) | [CYBLE_EVT_LE_PING_AUTH_TIMEOUT](#cyble_evt_le_ping_auth_timeout) |
| [Generic](#generic-events) | [0x00FF](#cyble_evt_max) | [CYBLE_EVT_MAX](#cyble_evt_max) |
| [GATT Service Events](#gatt_service_events) | [0x0104](#cyble_evt_gatts_indication_enabled) | [CYBLE_EVT_GATTS_INDICATION_ENABLED](#cyble_evt_gatts_indication_enabled) |
| [GATT Service Events](#gatt_service_events) | [0x0105](#cyble_evt_gatts_indication_disabled) | [CYBLE_EVT_GATTS_INDICATION_DISABLED](#cyble_evt_gatts_indication_disabled) |
| [GATT Service Events](#gatt_service_events) | [0x0106](#cyble_evt_gattc_indication) | [CYBLE_EVT_GATTC_INDICATION](#cyble_evt_gattc_indication) |
| [Service Discovery Events](#service_discovery_events) | [0x0107](#cyble_evt_gattc_srvc_discovery_failed) | [CYBLE_EVT_GATTC_SRVC_DISCOVERY_FAILED](#cyble_evt_gattc_srvc_discovery_failed) |
| [Service Discovery Events](#service_discovery_events) | [0x0108](#cyble_evt_gattc_incl_discovery_failed) | [CYBLE_EVT_GATTC_INCL_DISCOVERY_FAILED](#cyble_evt_gattc_incl_discovery_failed) |
| [Service Discovery Events](#service_discovery_events) | [0x0109](#cyble_evt_gattc_char_discovery_failed) | [CYBLE_EVT_GATTC_CHAR_DISCOVERY_FAILED](#cyble_evt_gattc_char_discovery_failed) |
| [Service Discovery Events](#service_discovery_events) | [0x010A](#cyble_evt_gattc_descr_discovery_failed) | [CYBLE_EVT_GATTC_DESCR_DISCOVERY_FAILED](#cyble_evt_gattc_descr_discovery_failed) |
| [Service Discovery Events](#service_discovery_events) | [0x010B](#cyble_evt_gattc_srvc_duplication) | [CYBLE_EVT_GATTC_SRVC_DUPLICATION](#cyble_evt_gattc_srvc_duplication) |
| [Service Discovery Events](#service_discovery_events) | [0x010C](#cyble_evt_gattc_char_duplication) | [CYBLE_EVT_GATTC_CHAR_DUPLICATION](#cyble_evt_gattc_char_duplication) |
| [Service Discovery Events](#service_discovery_events) | [0x010D](#cyble_evt_gattc_descr_duplication) | [CYBLE_EVT_GATTC_DESCR_DUPLICATION](#cyble_evt_gattc_descr_duplication) |
| [Service Discovery Events](#service_discovery_events) | [0x010E](#cyble_evt_gattc_srvc_discovery_complete) | [CYBLE_EVT_GATTC_SRVC_DISCOVERY_COMPLETE](#cyble_evt_gattc_srvc_discovery_complete) |
| [Service Discovery Events](#service_discovery_events) | [0x010F](#cyble_evt_gattc_incl_discovery_complete) | [CYBLE_EVT_GATTC_INCL_DISCOVERY_COMPLETE](#cyble_evt_gattc_incl_discovery_complete) |
| [Service Discovery Events](#service_discovery_events) | [0x0110](#cyble_evt_gattc_char_discovery_complete) | [CYBLE_EVT_GATTC_CHAR_DISCOVERY_COMPLETE](#cyble_evt_gattc_char_discovery_complete) |
| [Service Discovery Events](#service_discovery_events) | [0x0111](#cyble_evt_gattc_discovery_complete) | [CYBLE_EVT_GATTC_DISCOVERY_COMPLETE](#cyble_evt_gattc_discovery_complete) |
| [ANCS Service Events](#ancs_service_events) | [0x0112](#cyble_evt_ancss_notification_enabled) | [CYBLE_EVT_ANCSS_NOTIFICATION_ENABLED](#cyble_evt_ancss_notification_enabled) |
| [ANCS Service Events](#ancs_service_events) | [0x0113](#cyble_evt_ancss_notification_disabled) | [CYBLE_EVT_ANCSS_NOTIFICATION_DISABLED](#cyble_evt_ancss_notification_disabled) |
| [ANCS Service Events](#ancs_service_events) | [0x0114](#cyble_evt_ancss_write_char) | [CYBLE_EVT_ANCSS_WRITE_CHAR](#cyble_evt_ancss_write_char) |
| [ANCS Service Events](#ancs_service_events) | [0x0115](#cyble_evt_ancsc_notification) | [CYBLE_EVT_ANCSC_NOTIFICATION](#cyble_evt_ancsc_notification) |
| [ANCS Service Events](#ancs_service_events) | [0x0116](#cyble_evt_ancsc_read_char_response) | [CYBLE_EVT_ANCSC_READ_CHAR_RESPONSE](#cyble_evt_ancsc_read_char_response) |
| [ANCS Service Events](#ancs_service_events) | [0x0117](#cyble_evt_ancsc_write_char_response) | [CYBLE_EVT_ANCSC_WRITE_CHAR_RESPONSE](#cyble_evt_ancsc_write_char_response) |
| [ANCS Service Events](#ancs_service_events) | [0x0118](#cyble_evt_ancsc_read_descr_response) | [CYBLE_EVT_ANCSC_READ_DESCR_RESPONSE](#cyble_evt_ancsc_read_descr_response) |
| [ANCS Service Events](#ancs_service_events) | [0x0119](#cyble_evt_ancsc_write_descr_response) | [CYBLE_EVT_ANCSC_WRITE_DESCR_RESPONSE](#cyble_evt_ancsc_write_descr_response) |
| [ANCS Service Events](#ancs_service_events) | [0x011A](#cyble_evt_ancsc_error_response) | [CYBLE_EVT_ANCSC_ERROR_RESPONSE](#cyble_evt_ancsc_error_response) |
| [ANS Service Events](#ans_service_events) | [0x011B](#cyble_evt_anss_notification_enabled) | [CYBLE_EVT_ANSS_NOTIFICATION_ENABLED](#cyble_evt_anss_notification_enabled) |
| [ANS Service Events](#ans_service_events) | [0x011C](#cyble_evt_anss_notification_disabled) | [CYBLE_EVT_ANSS_NOTIFICATION_DISABLED](#cyble_evt_anss_notification_disabled) |
| [ANS Service Events](#ans_service_events) | [0x011D](#cyble_evt_anss_char_write) | [CYBLE_EVT_ANSS_CHAR_WRITE](#cyble_evt_anss_char_write) |
| [ANS Service Events](#ans_service_events) | [0x011E](#cyble_evt_ansc_notification) | [CYBLE_EVT_ANSC_NOTIFICATION](#cyble_evt_ansc_notification) |
| [ANS Service Events](#ans_service_events) | [0x011F](#cyble_evt_ansc_read_char_response) | [CYBLE_EVT_ANSC_READ_CHAR_RESPONSE](#cyble_evt_ansc_read_char_response) |
| [ANS Service Events](#ans_service_events) | [0x0120](#cyble_evt_ansc_write_char_response) | [CYBLE_EVT_ANSC_WRITE_CHAR_RESPONSE](#cyble_evt_ansc_write_char_response) |
| [ANS Service Events](#ans_service_events) | [0x0121](#cyble_evt_ansc_read_descr_response) | [CYBLE_EVT_ANSC_READ_DESCR_RESPONSE](#cyble_evt_ansc_read_descr_response) |
| [ANS Service Events](#ans_service_events) | [0x0122](#cyble_evt_ansc_write_descr_response) | [CYBLE_EVT_ANSC_WRITE_DESCR_RESPONSE](#cyble_evt_ansc_write_descr_response) |
| [BAS Service Events](#bas_service_events) | [0x0123](#cyble_evt_bass_notification_enabled) | [CYBLE_EVT_BASS_NOTIFICATION_ENABLED](#cyble_evt_bass_notification_enabled) |
| [BAS Service Events](#bas_service_events) | [0x0124](#cyble_evt_bass_notification_disabled) | [CYBLE_EVT_BASS_NOTIFICATION_DISABLED](#cyble_evt_bass_notification_disabled) |
| [BAS Service Events](#bas_service_events) | [0x0125](#cyble_evt_basc_notification) | [CYBLE_EVT_BASC_NOTIFICATION](#cyble_evt_basc_notification) |
| [BAS Service Events](#bas_service_events) | [0x0126](#cyble_evt_basc_read_char_response) | [CYBLE_EVT_BASC_READ_CHAR_RESPONSE](#cyble_evt_basc_read_char_response) |
| [BAS Service Events](#bas_service_events) | [0x0127](#cyble_evt_basc_read_descr_response) | [CYBLE_EVT_BASC_READ_DESCR_RESPONSE](#cyble_evt_basc_read_descr_response) |
| [BAS Service Events](#bas_service_events) | [0x0128](#cyble_evt_basc_write_descr_response) | [CYBLE_EVT_BASC_WRITE_DESCR_RESPONSE](#cyble_evt_basc_write_descr_response) |
| [Body Composition Service Events](#body_composition_service_events) | [0x0129](#cyble_evt_bcss_indication_enabled) | [CYBLE_EVT_BCSS_INDICATION_ENABLED](#cyble_evt_bcss_indication_enabled) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012A](#cyble_evt_bcss_indication_disabled) | [CYBLE_EVT_BCSS_INDICATION_DISABLED](#cyble_evt_bcss_indication_disabled) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012B](#cyble_evt_bcss_indication_confirmed) | [CYBLE_EVT_BCSS_INDICATION_CONFIRMED](#cyble_evt_bcss_indication_confirmed) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012C](#cyble_evt_bcsc_indication) | [CYBLE_EVT_BCSC_INDICATION](#cyble_evt_bcsc_indication) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012D](#cyble_evt_bcsc_read_char_response) | [CYBLE_EVT_BCSC_READ_CHAR_RESPONSE](#cyble_evt_bcsc_read_char_response) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012E](#cyble_evt_bcsc_read_descr_response) | [CYBLE_EVT_BCSC_READ_DESCR_RESPONSE](#cyble_evt_bcsc_read_descr_response) |
| [Body Composition Service Events](#body_composition_service_events) | [0x012F](#cyble_evt_bcsc_write_descr_response) | [CYBLE_EVT_BCSC_WRITE_DESCR_RESPONSE](#cyble_evt_bcsc_write_descr_response) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0130](#cyble_evt_blss_indication_enabled) | [CYBLE_EVT_BLSS_INDICATION_ENABLED](#cyble_evt_blss_indication_enabled) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0131](#cyble_evt_blss_indication_disabled) | [CYBLE_EVT_BLSS_INDICATION_DISABLED](#cyble_evt_blss_indication_disabled) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0132](#cyble_evt_blss_indication_confirmed) | [CYBLE_EVT_BLSS_INDICATION_CONFIRMED](#cyble_evt_blss_indication_confirmed) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0133](#cyble_evt_blss_notification_enabled) | [CYBLE_EVT_BLSS_NOTIFICATION_ENABLED](#cyble_evt_blss_notification_enabled) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0134](#cyble_evt_blss_notification_disabled) | [CYBLE_EVT_BLSS_NOTIFICATION_DISABLED](#cyble_evt_blss_notification_disabled) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0135](#cyble_evt_blsc_indication) | [CYBLE_EVT_BLSC_INDICATION](#cyble_evt_blsc_indication) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0136](#cyble_evt_blsc_notification) | [CYBLE_EVT_BLSC_NOTIFICATION](#cyble_evt_blsc_notification) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0137](#cyble_evt_blsc_read_char_response) | [CYBLE_EVT_BLSC_READ_CHAR_RESPONSE](#cyble_evt_blsc_read_char_response) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0138](#cyble_evt_blsc_read_descr_response) | [CYBLE_EVT_BLSC_READ_DESCR_RESPONSE](#cyble_evt_blsc_read_descr_response) |
| [Blood Pressure Service Events](#blood_pressure_service_events) | [0x0139](#cyble_evt_blsc_write_descr_response) | [CYBLE_EVT_BLSC_WRITE_DESCR_RESPONSE](#cyble_evt_blsc_write_descr_response) |
| [Bond Management Service Events](#bond_management_service_events) | [0x013A](#cyble_evt_bmss_write_char) | [CYBLE_EVT_BMSS_WRITE_CHAR](#cyble_evt_bmss_write_char) |
| [Bond Management Service Events](#bond_management_service_events) | [0x013B](#cyble_evt_bmsc_read_char_response) | [CYBLE_EVT_BMSC_READ_CHAR_RESPONSE](#cyble_evt_bmsc_read_char_response) |
| [Bond Management Service Events](#bond_management_service_events) | [0x013C](#cyble_evt_bmsc_write_char_response) | [CYBLE_EVT_BMSC_WRITE_CHAR_RESPONSE](#cyble_evt_bmsc_write_char_response) |
| [Bond Management Service Events](#bond_management_service_events) | [0x013D](#cyble_evt_bmsc_read_descr_response) | [CYBLE_EVT_BMSC_READ_DESCR_RESPONSE](#cyble_evt_bmsc_read_descr_response) |
| [CGM Service Events](#cgm_service_events) | [0x013E](#cyble_evt_cgmss_indication_enabled) | [CYBLE_EVT_CGMSS_INDICATION_ENABLED](#cyble_evt_cgmss_indication_enabled) |
| [CGM Service Events](#cgm_service_events) | [0x013F](#cyble_evt_cgmss_indication_disabled) | [CYBLE_EVT_CGMSS_INDICATION_DISABLED](#cyble_evt_cgmss_indication_disabled) |
| [CGM Service Events](#cgm_service_events) | [0x0140](#cyble_evt_cgmss_indication_confirmed) | [CYBLE_EVT_CGMSS_INDICATION_CONFIRMED](#cyble_evt_cgmss_indication_confirmed) |
| [CGM Service Events](#cgm_service_events) | [0x0141](#cyble_evt_cgmss_notification_enabled) | [CYBLE_EVT_CGMSS_NOTIFICATION_ENABLED](#cyble_evt_cgmss_notification_enabled) |
| [CGM Service Events](#cgm_service_events) | [0x0142](#cyble_evt_cgmss_notification_disabled) | [CYBLE_EVT_CGMSS_NOTIFICATION_DISABLED](#cyble_evt_cgmss_notification_disabled) |
| [CGM Service Events](#cgm_service_events) | [0x0143](#cyble_evt_cgmss_write_char) | [CYBLE_EVT_CGMSS_WRITE_CHAR](#cyble_evt_cgmss_write_char) |
| [CGM Service Events](#cgm_service_events) | [0x0144](#cyble_evt_cgmsc_indication) | [CYBLE_EVT_CGMSC_INDICATION](#cyble_evt_cgmsc_indication) |
| [CGM Service Events](#cgm_service_events) | [0x0145](#cyble_evt_cgmsc_notification) | [CYBLE_EVT_CGMSC_NOTIFICATION](#cyble_evt_cgmsc_notification) |
| [CGM Service Events](#cgm_service_events) | [0x0146](#cyble_evt_cgmsc_read_char_response) | [CYBLE_EVT_CGMSC_READ_CHAR_RESPONSE](#cyble_evt_cgmsc_read_char_response) |
| [CGM Service Events](#cgm_service_events) | [0x0147](#cyble_evt_cgmsc_write_char_response) | [CYBLE_EVT_CGMSC_WRITE_CHAR_RESPONSE](#cyble_evt_cgmsc_write_char_response) |
| [CGM Service Events](#cgm_service_events) | [0x0148](#cyble_evt_cgmsc_read_descr_response) | [CYBLE_EVT_CGMSC_READ_DESCR_RESPONSE](#cyble_evt_cgmsc_read_descr_response) |
| [CGM Service Events](#cgm_service_events) | [0x0149](#cyble_evt_cgmsc_write_descr_response) | [CYBLE_EVT_CGMSC_WRITE_DESCR_RESPONSE](#cyble_evt_cgmsc_write_descr_response) |
| [CPS Service Events](#cps_service_events) | [0x014A](#cyble_evt_cpss_notification_enabled) | [CYBLE_EVT_CPSS_NOTIFICATION_ENABLED](#cyble_evt_cpss_notification_enabled) |
| [CPS Service Events](#cps_service_events) | [0x014B](#cyble_evt_cpss_notification_disabled) | [CYBLE_EVT_CPSS_NOTIFICATION_DISABLED](#cyble_evt_cpss_notification_disabled) |
| [CPS Service Events](#cps_service_events) | [0x014C](#cyble_evt_cpss_indication_enabled) | [CYBLE_EVT_CPSS_INDICATION_ENABLED](#cyble_evt_cpss_indication_enabled) |
| [CPS Service Events](#cps_service_events) | [0x014D](#cyble_evt_cpss_indication_disabled) | [CYBLE_EVT_CPSS_INDICATION_DISABLED](#cyble_evt_cpss_indication_disabled) |
| [CPS Service Events](#cps_service_events) | [0x014E](#cyble_evt_cpss_indication_confirmed) | [CYBLE_EVT_CPSS_INDICATION_CONFIRMED](#cyble_evt_cpss_indication_confirmed) |
| [CPS Service Events](#cps_service_events) | [0x014F](#cyble_evt_cpss_broadcast_enabled) | [CYBLE_EVT_CPSS_BROADCAST_ENABLED](#cyble_evt_cpss_broadcast_enabled) |
| [CPS Service Events](#cps_service_events) | [0x0150](#cyble_evt_cpss_broadcast_disabled) | [CYBLE_EVT_CPSS_BROADCAST_DISABLED](#cyble_evt_cpss_broadcast_disabled) |
| [CPS Service Events](#cps_service_events) | [0x0151](#cyble_evt_cpss_char_write) | [CYBLE_EVT_CPSS_CHAR_WRITE](#cyble_evt_cpss_char_write) |
| [CPS Service Events](#cps_service_events) | [0x0152](#cyble_evt_cpsc_notification) | [CYBLE_EVT_CPSC_NOTIFICATION](#cyble_evt_cpsc_notification) |
| [CPS Service Events](#cps_service_events) | [0x0153](#cyble_evt_cpsc_indication) | [CYBLE_EVT_CPSC_INDICATION](#cyble_evt_cpsc_indication) |
| [CPS Service Events](#cps_service_events) | [0x0154](#cyble_evt_cpsc_read_char_response) | [CYBLE_EVT_CPSC_READ_CHAR_RESPONSE](#cyble_evt_cpsc_read_char_response) |
| [CPS Service Events](#cps_service_events) | [0x0155](#cyble_evt_cpsc_write_char_response) | [CYBLE_EVT_CPSC_WRITE_CHAR_RESPONSE](#cyble_evt_cpsc_write_char_response) |
| [CPS Service Events](#cps_service_events) | [0x0156](#cyble_evt_cpsc_read_descr_response) | [CYBLE_EVT_CPSC_READ_DESCR_RESPONSE](#cyble_evt_cpsc_read_descr_response) |
| [CPS Service Events](#cps_service_events) | [0x0157](#cyble_evt_cpsc_write_descr_response) | [CYBLE_EVT_CPSC_WRITE_DESCR_RESPONSE](#cyble_evt_cpsc_write_descr_response) |
| [CPS Service Events](#cps_service_events) | [0x0158](#cyble_evt_cpsc_scan_progress_result) | [CYBLE_EVT_CPSC_SCAN_PROGRESS_RESULT](#cyble_evt_cpsc_scan_progress_result) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0159](#cyble_evt_cscss_notification_enabled) | [CYBLE_EVT_CSCSS_NOTIFICATION_ENABLED](#cyble_evt_cscss_notification_enabled) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015A](#cyble_evt_cscss_notification_disabled) | [CYBLE_EVT_CSCSS_NOTIFICATION_DISABLED](#cyble_evt_cscss_notification_disabled) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015B](#cyble_evt_cscss_indication_enabled) | [CYBLE_EVT_CSCSS_INDICATION_ENABLED](#cyble_evt_cscss_indication_enabled) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015C](#cyble_evt_cscss_indication_disabled) | [CYBLE_EVT_CSCSS_INDICATION_DISABLED](#cyble_evt_cscss_indication_disabled) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015D](#cyble_evt_cscss_indication_confirmation) | [CYBLE_EVT_CSCSS_INDICATION_CONFIRMATION](#cyble_evt_cscss_indication_confirmation) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015E](#cyble_evt_cscss_char_write) | [CYBLE_EVT_CSCSS_CHAR_WRITE](#cyble_evt_cscss_char_write) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x015F](#cyble_evt_cscsc_notification) | [CYBLE_EVT_CSCSC_NOTIFICATION](#cyble_evt_cscsc_notification) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0160](#cyble_evt_cscsc_indication) | [CYBLE_EVT_CSCSC_INDICATION](#cyble_evt_cscsc_indication) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0161](#cyble_evt_cscsc_read_char_response) | [CYBLE_EVT_CSCSC_READ_CHAR_RESPONSE](#cyble_evt_cscsc_read_char_response) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0162](#cyble_evt_cscsc_write_char_response) | [CYBLE_EVT_CSCSC_WRITE_CHAR_RESPONSE](#cyble_evt_cscsc_write_char_response) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0163](#cyble_evt_cscsc_read_descr_response) | [CYBLE_EVT_CSCSC_READ_DESCR_RESPONSE](#cyble_evt_cscsc_read_descr_response) |
| [Cycling Speed and Cadence Service Events](#cycling_speed_and_cadence_service_events) | [0x0164](#cyble_evt_cscsc_write_descr_response) | [CYBLE_EVT_CSCSC_WRITE_DESCR_RESPONSE](#cyble_evt_cscsc_write_descr_response) |
| [Current Time Service Events](#current_time_service_events) | [0x0165](#cyble_evt_ctss_notification_enabled) | [CYBLE_EVT_CTSS_NOTIFICATION_ENABLED](#cyble_evt_ctss_notification_enabled) |
| [Current Time Service Events](#current_time_service_events) | [0x0166](#cyble_evt_ctss_notification_disabled) | [CYBLE_EVT_CTSS_NOTIFICATION_DISABLED](#cyble_evt_ctss_notification_disabled) |
| [Current Time Service Events](#current_time_service_events) | [0x0167](#cyble_evt_ctss_char_write) | [CYBLE_EVT_CTSS_CHAR_WRITE](#cyble_evt_ctss_char_write) |
| [Current Time Service Events](#current_time_service_events) | [0x0168](#cyble_evt_ctsc_notification) | [CYBLE_EVT_CTSC_NOTIFICATION](#cyble_evt_ctsc_notification) |
| [Current Time Service Events](#current_time_service_events) | [0x0169](#cyble_evt_ctsc_read_char_response) | [CYBLE_EVT_CTSC_READ_CHAR_RESPONSE](#cyble_evt_ctsc_read_char_response) |
| [Current Time Service Events](#current_time_service_events) | [0x016A](#cyble_evt_ctsc_read_descr_response) | [CYBLE_EVT_CTSC_READ_DESCR_RESPONSE](#cyble_evt_ctsc_read_descr_response) |
| [Current Time Service Events](#current_time_service_events) | [0x016B](#cyble_evt_ctsc_write_descr_response) | [CYBLE_EVT_CTSC_WRITE_DESCR_RESPONSE](#cyble_evt_ctsc_write_descr_response) |
| [Current Time Service Events](#current_time_service_events) | [0x016C](#cyble_evt_ctsc_write_char_response) | [CYBLE_EVT_CTSC_WRITE_CHAR_RESPONSE](#cyble_evt_ctsc_write_char_response) |
| [DIS Service Events](#dis_service_events) | [0x016D](#cyble_evt_disc_read_char_response) | [CYBLE_EVT_DISC_READ_CHAR_RESPONSE](#cyble_evt_disc_read_char_response) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x016E](#cyble_evt_esss_notification_enabled) | [CYBLE_EVT_ESSS_NOTIFICATION_ENABLED](#cyble_evt_esss_notification_enabled) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x016F](#cyble_evt_esss_notification_disabled) | [CYBLE_EVT_ESSS_NOTIFICATION_DISABLED](#cyble_evt_esss_notification_disabled) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0170](#cyble_evt_esss_indication_enabled) | [CYBLE_EVT_ESSS_INDICATION_ENABLED](#cyble_evt_esss_indication_enabled) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0171](#cyble_evt_esss_indication_disabled) | [CYBLE_EVT_ESSS_INDICATION_DISABLED](#cyble_evt_esss_indication_disabled) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0172](#cyble_evt_esss_indication_confirmation) | [CYBLE_EVT_ESSS_INDICATION_CONFIRMATION](#cyble_evt_esss_indication_confirmation) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0173](#cyble_evt_esss_char_write) | [CYBLE_EVT_ESSS_CHAR_WRITE](#cyble_evt_esss_char_write) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0174](#cyble_evt_esss_exec_write_req) | [CYBLE_EVT_ESSS_EXEC_WRITE_REQ](#cyble_evt_esss_exec_write_req) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0175](#cyble_evt_esss_descr_write) | [CYBLE_EVT_ESSS_DESCR_WRITE](#cyble_evt_esss_descr_write) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0176](#cyble_evt_essc_notification) | [CYBLE_EVT_ESSC_NOTIFICATION](#cyble_evt_essc_notification) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0177](#cyble_evt_essc_indication) | [CYBLE_EVT_ESSC_INDICATION](#cyble_evt_essc_indication) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0178](#cyble_evt_essc_read_char_response) | [CYBLE_EVT_ESSC_READ_CHAR_RESPONSE](#cyble_evt_essc_read_char_response) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x0179](#cyble_evt_essc_write_char_response) | [CYBLE_EVT_ESSC_WRITE_CHAR_RESPONSE](#cyble_evt_essc_write_char_response) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x017A](#cyble_evt_essc_read_descr_response) | [CYBLE_EVT_ESSC_READ_DESCR_RESPONSE](#cyble_evt_essc_read_descr_response) |
| [Environmental Sensing Service Events](#environmental_sensing_service_events) | [0x017B](#cyble_evt_essc_write_descr_response) | [CYBLE_EVT_ESSC_WRITE_DESCR_RESPONSE](#cyble_evt_essc_write_descr_response) |
| [Glucose Service Events](#glucose_service_events) | [0x017C](#cyble_evt_glss_indication_enabled) | [CYBLE_EVT_GLSS_INDICATION_ENABLED](#cyble_evt_glss_indication_enabled) |
| [Glucose Service Events](#glucose_service_events) | [0x017D](#cyble_evt_glss_indication_disabled) | [CYBLE_EVT_GLSS_INDICATION_DISABLED](#cyble_evt_glss_indication_disabled) |
| [Glucose Service Events](#glucose_service_events) | [0x017E](#cyble_evt_glss_indication_confirmed) | [CYBLE_EVT_GLSS_INDICATION_CONFIRMED](#cyble_evt_glss_indication_confirmed) |
| [Glucose Service Events](#glucose_service_events) | [0x017F](#cyble_evt_glss_notification_enabled) | [CYBLE_EVT_GLSS_NOTIFICATION_ENABLED](#cyble_evt_glss_notification_enabled) |
| [Glucose Service Events](#glucose_service_events) | [0x0180](#cyble_evt_glss_notification_disabled) | [CYBLE_EVT_GLSS_NOTIFICATION_DISABLED](#cyble_evt_glss_notification_disabled) |
| [Glucose Service Events](#glucose_service_events) | [0x0181](#cyble_evt_glss_write_char) | [CYBLE_EVT_GLSS_WRITE_CHAR](#cyble_evt_glss_write_char) |
| [Glucose Service Events](#glucose_service_events) | [0x0182](#cyble_evt_glsc_indication) | [CYBLE_EVT_GLSC_INDICATION](#cyble_evt_glsc_indication) |
| [Glucose Service Events](#glucose_service_events) | [0x0183](#cyble_evt_glsc_notification) | [CYBLE_EVT_GLSC_NOTIFICATION](#cyble_evt_glsc_notification) |
| [Glucose Service Events](#glucose_service_events) | [0x0184](#cyble_evt_glsc_read_char_response) | [CYBLE_EVT_GLSC_READ_CHAR_RESPONSE](#cyble_evt_glsc_read_char_response) |
| [Glucose Service Events](#glucose_service_events) | [0x0185](#cyble_evt_glsc_write_char_response) | [CYBLE_EVT_GLSC_WRITE_CHAR_RESPONSE](#cyble_evt_glsc_write_char_response) |
| [Glucose Service Events](#glucose_service_events) | [0x0186](#cyble_evt_glsc_read_descr_response) | [CYBLE_EVT_GLSC_READ_DESCR_RESPONSE](#cyble_evt_glsc_read_descr_response) |
| [Glucose Service Events](#glucose_service_events) | [0x0187](#cyble_evt_glsc_write_descr_response) | [CYBLE_EVT_GLSC_WRITE_DESCR_RESPONSE](#cyble_evt_glsc_write_descr_response) |
| [HIDS Service Events](#hids_service_events) | [0x0188](#cyble_evt_hidss_notification_enabled) | [CYBLE_EVT_HIDSS_NOTIFICATION_ENABLED](#cyble_evt_hidss_notification_enabled) |
| [HIDS Service Events](#hids_service_events) | [0x0189](#cyble_evt_hidss_notification_disabled) | [CYBLE_EVT_HIDSS_NOTIFICATION_DISABLED](#cyble_evt_hidss_notification_disabled) |
| [HIDS Service Events](#hids_service_events) | [0x018A](#cyble_evt_hidss_boot_mode_enter) | [CYBLE_EVT_HIDSS_BOOT_MODE_ENTER](#cyble_evt_hidss_boot_mode_enter) |
| [HIDS Service Events](#hids_service_events) | [0x018B](#cyble_evt_hidss_report_mode_enter) | [CYBLE_EVT_HIDSS_REPORT_MODE_ENTER](#cyble_evt_hidss_report_mode_enter) |
| [HIDS Service Events](#hids_service_events) | [0x018C](#cyble_evt_hidss_suspend) | [CYBLE_EVT_HIDSS_SUSPEND](#cyble_evt_hidss_suspend) |
| [HIDS Service Events](#hids_service_events) | [0x018D](#cyble_evt_hidss_exit_suspend) | [CYBLE_EVT_HIDSS_EXIT_SUSPEND](#cyble_evt_hidss_exit_suspend) |
| [HIDS Service Events](#hids_service_events) | [0x018E](#cyble_evt_hidss_report_char_write) | [CYBLE_EVT_HIDSS_REPORT_CHAR_WRITE](#cyble_evt_hidss_report_char_write) |
| [HIDS Service Events](#hids_service_events) | [0x018F](#cyble_evt_hidsc_notification) | [CYBLE_EVT_HIDSC_NOTIFICATION](#cyble_evt_hidsc_notification) |
| [HIDS Service Events](#hids_service_events) | [0x0190](#cyble_evt_hidsc_read_char_response) | [CYBLE_EVT_HIDSC_READ_CHAR_RESPONSE](#cyble_evt_hidsc_read_char_response) |
| [HIDS Service Events](#hids_service_events) | [0x0191](#cyble_evt_hidsc_write_char_response) | [CYBLE_EVT_HIDSC_WRITE_CHAR_RESPONSE](#cyble_evt_hidsc_write_char_response) |
| [HIDS Service Events](#hids_service_events) | [0x0192](#cyble_evt_hidsc_read_descr_response) | [CYBLE_EVT_HIDSC_READ_DESCR_RESPONSE](#cyble_evt_hidsc_read_descr_response) |
| [HIDS Service Events](#hids_service_events) | [0x0193](#cyble_evt_hidsc_write_descr_response) | [CYBLE_EVT_HIDSC_WRITE_DESCR_RESPONSE](#cyble_evt_hidsc_write_descr_response) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0194](#cyble_evt_hpss_notification_enabled) | [CYBLE_EVT_HPSS_NOTIFICATION_ENABLED](#cyble_evt_hpss_notification_enabled) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0195](#cyble_evt_hpss_notification_disabled) | [CYBLE_EVT_HPSS_NOTIFICATION_DISABLED](#cyble_evt_hpss_notification_disabled) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0196](#cyble_evt_hpss_char_write) | [CYBLE_EVT_HPSS_CHAR_WRITE](#cyble_evt_hpss_char_write) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0197](#cyble_evt_hpsc_notification) | [CYBLE_EVT_HPSC_NOTIFICATION](#cyble_evt_hpsc_notification) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0198](#cyble_evt_hpsc_read_char_response) | [CYBLE_EVT_HPSC_READ_CHAR_RESPONSE](#cyble_evt_hpsc_read_char_response) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x0199](#cyble_evt_hpsc_read_descr_response) | [CYBLE_EVT_HPSC_READ_DESCR_RESPONSE](#cyble_evt_hpsc_read_descr_response) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x019A](#cyble_evt_hpsc_write_descr_response) | [CYBLE_EVT_HPSC_WRITE_DESCR_RESPONSE](#cyble_evt_hpsc_write_descr_response) |
| [HTTP Proxy Service Events](#http_proxy_service_events) | [0x019B](#cyble_evt_hpsc_write_char_response) | [CYBLE_EVT_HPSC_WRITE_CHAR_RESPONSE](#cyble_evt_hpsc_write_char_response) |
| [HRS Service Events](#hrs_service_events) | [0x019C](#cyble_evt_hrss_energy_expended_reset) | [CYBLE_EVT_HRSS_ENERGY_EXPENDED_RESET](#cyble_evt_hrss_energy_expended_reset) |
| [HRS Service Events](#hrs_service_events) | [0x019D](#cyble_evt_hrss_notification_enabled) | [CYBLE_EVT_HRSS_NOTIFICATION_ENABLED](#cyble_evt_hrss_notification_enabled) |
| [HRS Service Events](#hrs_service_events) | [0x019E](#cyble_evt_hrss_notification_disabled) | [CYBLE_EVT_HRSS_NOTIFICATION_DISABLED](#cyble_evt_hrss_notification_disabled) |
| [HRS Service Events](#hrs_service_events) | [0x019F](#cyble_evt_hrsc_notification) | [CYBLE_EVT_HRSC_NOTIFICATION](#cyble_evt_hrsc_notification) |
| [HRS Service Events](#hrs_service_events) | [0x01A0](#cyble_evt_hrsc_read_char_response) | [CYBLE_EVT_HRSC_READ_CHAR_RESPONSE](#cyble_evt_hrsc_read_char_response) |
| [HRS Service Events](#hrs_service_events) | [0x01A1](#cyble_evt_hrsc_write_char_response) | [CYBLE_EVT_HRSC_WRITE_CHAR_RESPONSE](#cyble_evt_hrsc_write_char_response) |
| [HRS Service Events](#hrs_service_events) | [0x01A2](#cyble_evt_hrsc_read_descr_response) | [CYBLE_EVT_HRSC_READ_DESCR_RESPONSE](#cyble_evt_hrsc_read_descr_response) |
| [HRS Service Events](#hrs_service_events) | [0x01A3](#cyble_evt_hrsc_write_descr_response) | [CYBLE_EVT_HRSC_WRITE_DESCR_RESPONSE](#cyble_evt_hrsc_write_descr_response) |
| [HTS Service Events](#hts_service_events) | [0x01A4](#cyble_evt_htss_notification_enabled) | [CYBLE_EVT_HTSS_NOTIFICATION_ENABLED](#cyble_evt_htss_notification_enabled) |
| [HTS Service Events](#hts_service_events) | [0x01A5](#cyble_evt_htss_notification_disabled) | [CYBLE_EVT_HTSS_NOTIFICATION_DISABLED](#cyble_evt_htss_notification_disabled) |
| [HTS Service Events](#hts_service_events) | [0x01A6](#cyble_evt_htss_indication_enabled) | [CYBLE_EVT_HTSS_INDICATION_ENABLED](#cyble_evt_htss_indication_enabled) |
| [HTS Service Events](#hts_service_events) | [0x01A7](#cyble_evt_htss_indication_disabled) | [CYBLE_EVT_HTSS_INDICATION_DISABLED](#cyble_evt_htss_indication_disabled) |
| [HTS Service Events](#hts_service_events) | [0x01A8](#cyble_evt_htss_indication_confirmed) | [CYBLE_EVT_HTSS_INDICATION_CONFIRMED](#cyble_evt_htss_indication_confirmed) |
| [HTS Service Events](#hts_service_events) | [0x01A9](#cyble_evt_htss_char_write) | [CYBLE_EVT_HTSS_CHAR_WRITE](#cyble_evt_htss_char_write) |
| [HTS Service Events](#hts_service_events) | [0x01AA](#cyble_evt_htsc_notification) | [CYBLE_EVT_HTSC_NOTIFICATION](#cyble_evt_htsc_notification) |
| [HTS Service Events](#hts_service_events) | [0x01AB](#cyble_evt_htsc_indication) | [CYBLE_EVT_HTSC_INDICATION](#cyble_evt_htsc_indication) |
| [HTS Service Events](#hts_service_events) | [0x01AC](#cyble_evt_htsc_read_char_response) | [CYBLE_EVT_HTSC_READ_CHAR_RESPONSE](#cyble_evt_htsc_read_char_response) |
| [HTS Service Events](#hts_service_events) | [0x01AD](#cyble_evt_htsc_write_char_response) | [CYBLE_EVT_HTSC_WRITE_CHAR_RESPONSE](#cyble_evt_htsc_write_char_response) |
| [HTS Service Events](#hts_service_events) | [0x01AE](#cyble_evt_htsc_read_descr_response) | [CYBLE_EVT_HTSC_READ_DESCR_RESPONSE](#cyble_evt_htsc_read_descr_response) |
| [HTS Service Events](#hts_service_events) | [0x01AF](#cyble_evt_htsc_write_descr_response) | [CYBLE_EVT_HTSC_WRITE_DESCR_RESPONSE](#cyble_evt_htsc_write_descr_response) |
| [Immediate Alert Service Events](#immediate_alert_service_events) | [0x01B0](#cyble_evt_iass_write_char_cmd) | [CYBLE_EVT_IASS_WRITE_CHAR_CMD](#cyble_evt_iass_write_char_cmd) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B1](#cyble_evt_ipss_read_char) | [CYBLE_EVT_IPSS_READ_CHAR](#cyble_evt_ipss_read_char) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B2](#cyble_evt_ipss_write_char) | [CYBLE_EVT_IPSS_WRITE_CHAR](#cyble_evt_ipss_write_char) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B3](#cyble_evt_ipss_write_char_cmd) | [CYBLE_EVT_IPSS_WRITE_CHAR_CMD](#cyble_evt_ipss_write_char_cmd) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B4](#cyble_evt_ipsc_read_char_response) | [CYBLE_EVT_IPSC_READ_CHAR_RESPONSE](#cyble_evt_ipsc_read_char_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B5](#cyble_evt_ipsc_read_multiple_char_response) | [CYBLE_EVT_IPSC_READ_MULTIPLE_CHAR_RESPONSE](#cyble_evt_ipsc_read_multiple_char_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B6](#cyble_evt_ipsc_write_char_response) | [CYBLE_EVT_IPSC_WRITE_CHAR_RESPONSE](#cyble_evt_ipsc_write_char_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B7](#cyble_evt_ipsc_read_descr_response) | [CYBLE_EVT_IPSC_READ_DESCR_RESPONSE](#cyble_evt_ipsc_read_descr_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B8](#cyble_evt_ipsc_write_descr_response) | [CYBLE_EVT_IPSC_WRITE_DESCR_RESPONSE](#cyble_evt_ipsc_write_descr_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01B9](#cyble_evt_ipsc_error_response) | [CYBLE_EVT_IPSC_ERROR_RESPONSE](#cyble_evt_ipsc_error_response) |
| [Indoor Positioning Service Events](#indoor_positioning_service_events) | [0x01BA](#cyble_evt_ipsc_read_blob_rsp) | [CYBLE_EVT_IPSC_READ_BLOB_RSP](#cyble_evt_ipsc_read_blob_rsp) |
| [Link Loss Service Events](#link_loss_service_events) | [0x01BB](#cyble_evt_llss_write_char_req) | [CYBLE_EVT_LLSS_WRITE_CHAR_REQ](#cyble_evt_llss_write_char_req) |
| [Link Loss Service Events](#link_loss_service_events) | [0x01BC](#cyble_evt_llsc_read_char_response) | [CYBLE_EVT_LLSC_READ_CHAR_RESPONSE](#cyble_evt_llsc_read_char_response) |
| [Link Loss Service Events](#link_loss_service_events) | [0x01BD](#cyble_evt_llsc_write_char_response) | [CYBLE_EVT_LLSC_WRITE_CHAR_RESPONSE](#cyble_evt_llsc_write_char_response) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01BE](#cyble_evt_lnss_indication_enabled) | [CYBLE_EVT_LNSS_INDICATION_ENABLED](#cyble_evt_lnss_indication_enabled) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01BF](#cyble_evt_lnss_indication_disabled) | [CYBLE_EVT_LNSS_INDICATION_DISABLED](#cyble_evt_lnss_indication_disabled) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C0](#cyble_evt_lnss_indication_confirmed) | [CYBLE_EVT_LNSS_INDICATION_CONFIRMED](#cyble_evt_lnss_indication_confirmed) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C1](#cyble_evt_lnss_notification_enabled) | [CYBLE_EVT_LNSS_NOTIFICATION_ENABLED](#cyble_evt_lnss_notification_enabled) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C2](#cyble_evt_lnss_notification_disabled) | [CYBLE_EVT_LNSS_NOTIFICATION_DISABLED](#cyble_evt_lnss_notification_disabled) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C3](#cyble_evt_lnss_write_char) | [CYBLE_EVT_LNSS_WRITE_CHAR](#cyble_evt_lnss_write_char) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C4](#cyble_evt_lnsc_indication) | [CYBLE_EVT_LNSC_INDICATION](#cyble_evt_lnsc_indication) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C5](#cyble_evt_lnsc_notification) | [CYBLE_EVT_LNSC_NOTIFICATION](#cyble_evt_lnsc_notification) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C6](#cyble_evt_lnsc_read_char_response) | [CYBLE_EVT_LNSC_READ_CHAR_RESPONSE](#cyble_evt_lnsc_read_char_response) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C7](#cyble_evt_lnsc_write_char_response) | [CYBLE_EVT_LNSC_WRITE_CHAR_RESPONSE](#cyble_evt_lnsc_write_char_response) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C8](#cyble_evt_lnsc_read_descr_response) | [CYBLE_EVT_LNSC_READ_DESCR_RESPONSE](#cyble_evt_lnsc_read_descr_response) |
| [Location and Navigation Service Events](#location_and_navigation_service_events) | [0x01C9](#cyble_evt_lnsc_write_descr_response) | [CYBLE_EVT_LNSC_WRITE_DESCR_RESPONSE](#cyble_evt_lnsc_write_descr_response) |
| [Next DST Change Service Events](#next_dst_change_service_events) | [0x01CA](#cyble_evt_ndcsc_read_char_response) | [CYBLE_EVT_NDCSC_READ_CHAR_RESPONSE](#cyble_evt_ndcsc_read_char_response) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01CB](#cyble_evt_passs_notification_enabled) | [CYBLE_EVT_PASSS_NOTIFICATION_ENABLED](#cyble_evt_passs_notification_enabled) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01CC](#cyble_evt_passs_notification_disabled) | [CYBLE_EVT_PASSS_NOTIFICATION_DISABLED](#cyble_evt_passs_notification_disabled) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01CD](#cyble_evt_passs_write_char) | [CYBLE_EVT_PASSS_WRITE_CHAR](#cyble_evt_passs_write_char) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01CE](#cyble_evt_passc_notification) | [CYBLE_EVT_PASSC_NOTIFICATION](#cyble_evt_passc_notification) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01CF](#cyble_evt_passc_read_char_response) | [CYBLE_EVT_PASSC_READ_CHAR_RESPONSE](#cyble_evt_passc_read_char_response) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01D0](#cyble_evt_passc_write_char_response) | [CYBLE_EVT_PASSC_WRITE_CHAR_RESPONSE](#cyble_evt_passc_write_char_response) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01D1](#cyble_evt_passc_read_descr_response) | [CYBLE_EVT_PASSC_READ_DESCR_RESPONSE](#cyble_evt_passc_read_descr_response) |
| [Phone Alert Status Service Events](#phone_alert_status_service_events) | [0x01D2](#cyble_evt_passc_write_descr_response) | [CYBLE_EVT_PASSC_WRITE_DESCR_RESPONSE](#cyble_evt_passc_write_descr_response) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D3](#cyble_evt_rscss_notification_enabled) | [CYBLE_EVT_RSCSS_NOTIFICATION_ENABLED](#cyble_evt_rscss_notification_enabled) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D4](#cyble_evt_rscss_notification_disabled) | [CYBLE_EVT_RSCSS_NOTIFICATION_DISABLED](#cyble_evt_rscss_notification_disabled) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D5](#cyble_evt_rscss_indication_enabled) | [CYBLE_EVT_RSCSS_INDICATION_ENABLED](#cyble_evt_rscss_indication_enabled) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D6](#cyble_evt_rscss_indication_disabled) | [CYBLE_EVT_RSCSS_INDICATION_DISABLED](#cyble_evt_rscss_indication_disabled) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D7](#cyble_evt_rscss_indication_confirmation) | [CYBLE_EVT_RSCSS_INDICATION_CONFIRMATION](#cyble_evt_rscss_indication_confirmation) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D8](#cyble_evt_rscss_char_write) | [CYBLE_EVT_RSCSS_CHAR_WRITE](#cyble_evt_rscss_char_write) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01D9](#cyble_evt_rscsc_notification) | [CYBLE_EVT_RSCSC_NOTIFICATION](#cyble_evt_rscsc_notification) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01DA](#cyble_evt_rscsc_indication) | [CYBLE_EVT_RSCSC_INDICATION](#cyble_evt_rscsc_indication) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01DB](#cyble_evt_rscsc_read_char_response) | [CYBLE_EVT_RSCSC_READ_CHAR_RESPONSE](#cyble_evt_rscsc_read_char_response) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01DC](#cyble_evt_rscsc_write_char_response) | [CYBLE_EVT_RSCSC_WRITE_CHAR_RESPONSE](#cyble_evt_rscsc_write_char_response) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01DD](#cyble_evt_rscsc_read_descr_response) | [CYBLE_EVT_RSCSC_READ_DESCR_RESPONSE](#cyble_evt_rscsc_read_descr_response) |
| [Running Speed and Cadence Service Events](#running_speed_and_cadence_service_events) | [0x01DE](#cyble_evt_rscsc_write_descr_response) | [CYBLE_EVT_RSCSC_WRITE_DESCR_RESPONSE](#cyble_evt_rscsc_write_descr_response) |
| [Reference Time Update Service Events](#reference_time_update_service_events) | [0x01DF](#cyble_evt_rtuss_write_char_cmd) | [CYBLE_EVT_RTUSS_WRITE_CHAR_CMD](#cyble_evt_rtuss_write_char_cmd) |
| [Reference Time Update Service Events](#reference_time_update_service_events) | [0x01E0](#cyble_evt_rtusc_read_char_response) | [CYBLE_EVT_RTUSC_READ_CHAR_RESPONSE](#cyble_evt_rtusc_read_char_response) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E1](#cyble_evt_scpss_notification_enabled) | [CYBLE_EVT_SCPSS_NOTIFICATION_ENABLED](#cyble_evt_scpss_notification_enabled) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E2](#cyble_evt_scpss_notification_disabled) | [CYBLE_EVT_SCPSS_NOTIFICATION_DISABLED](#cyble_evt_scpss_notification_disabled) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E3](#cyble_evt_scpss_scan_int_win_char_write) | [CYBLE_EVT_SCPSS_SCAN_INT_WIN_CHAR_WRITE](#cyble_evt_scpss_scan_int_win_char_write) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E4](#cyble_evt_scpsc_notification) | [CYBLE_EVT_SCPSC_NOTIFICATION](#cyble_evt_scpsc_notification) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E5](#cyble_evt_scpsc_read_descr_response) | [CYBLE_EVT_SCPSC_READ_DESCR_RESPONSE](#cyble_evt_scpsc_read_descr_response) |
| [Scan Parameters Service Events](#scan_parameters_service_events) | [0x01E6](#cyble_evt_scpsc_write_descr_response) | [CYBLE_EVT_SCPSC_WRITE_DESCR_RESPONSE](#cyble_evt_scpsc_write_descr_response) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01E7](#cyble_evt_tpss_notification_enabled) | [CYBLE_EVT_TPSS_NOTIFICATION_ENABLED](#cyble_evt_tpss_notification_enabled) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01E8](#cyble_evt_tpss_notification_disabled) | [CYBLE_EVT_TPSS_NOTIFICATION_DISABLED](#cyble_evt_tpss_notification_disabled) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01E9](#cyble_evt_tpsc_notification) | [CYBLE_EVT_TPSC_NOTIFICATION](#cyble_evt_tpsc_notification) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01EA](#cyble_evt_tpsc_read_char_response) | [CYBLE_EVT_TPSC_READ_CHAR_RESPONSE](#cyble_evt_tpsc_read_char_response) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01EB](#cyble_evt_tpsc_read_descr_response) | [CYBLE_EVT_TPSC_READ_DESCR_RESPONSE](#cyble_evt_tpsc_read_descr_response) |
| [Tx Power Service Events](#tx_power_service_events) | [0x01EC](#cyble_evt_tpsc_write_descr_response) | [CYBLE_EVT_TPSC_WRITE_DESCR_RESPONSE](#cyble_evt_tpsc_write_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x01ED](#cyble_evt_udss_indication_enabled) | [CYBLE_EVT_UDSS_INDICATION_ENABLED](#cyble_evt_udss_indication_enabled) |
| [User Data Service Events](#user_data_service_events) | [0x01EE](#cyble_evt_udss_indication_disabled) | [CYBLE_EVT_UDSS_INDICATION_DISABLED](#cyble_evt_udss_indication_disabled) |
| [User Data Service Events](#user_data_service_events) | [0x01EF](#cyble_evt_udss_indication_confirmed) | [CYBLE_EVT_UDSS_INDICATION_CONFIRMED](#cyble_evt_udss_indication_confirmed) |
| [User Data Service Events](#user_data_service_events) | [0x01F0](#cyble_evt_udss_notification_enabled) | [CYBLE_EVT_UDSS_NOTIFICATION_ENABLED](#cyble_evt_udss_notification_enabled) |
| [User Data Service Events](#user_data_service_events) | [0x01F1](#cyble_evt_udss_notification_disabled) | [CYBLE_EVT_UDSS_NOTIFICATION_DISABLED](#cyble_evt_udss_notification_disabled) |
| [User Data Service Events](#user_data_service_events) | [0x01F2](#cyble_evt_udss_read_char) | [CYBLE_EVT_UDSS_READ_CHAR](#cyble_evt_udss_read_char) |
| [User Data Service Events](#user_data_service_events) | [0x01F3](#cyble_evt_udss_write_char) | [CYBLE_EVT_UDSS_WRITE_CHAR](#cyble_evt_udss_write_char) |
| [User Data Service Events](#user_data_service_events) | [0x01F4](#cyble_evt_udsc_indication) | [CYBLE_EVT_UDSC_INDICATION](#cyble_evt_udsc_indication) |
| [User Data Service Events](#user_data_service_events) | [0x01F5](#cyble_evt_udsc_notification) | [CYBLE_EVT_UDSC_NOTIFICATION](#cyble_evt_udsc_notification) |
| [User Data Service Events](#user_data_service_events) | [0x01F6](#cyble_evt_udsc_read_char_response) | [CYBLE_EVT_UDSC_READ_CHAR_RESPONSE](#cyble_evt_udsc_read_char_response) |
| [User Data Service Events](#user_data_service_events) | [0x01F7](#cyble_evt_udsc_write_char_response) | [CYBLE_EVT_UDSC_WRITE_CHAR_RESPONSE](#cyble_evt_udsc_write_char_response) |
| [User Data Service Events](#user_data_service_events) | [0x01F8](#cyble_evt_udsc_read_descr_response) | [CYBLE_EVT_UDSC_READ_DESCR_RESPONSE](#cyble_evt_udsc_read_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x01F9](#cyble_evt_udsc_write_descr_response) | [CYBLE_EVT_UDSC_WRITE_DESCR_RESPONSE](#cyble_evt_udsc_write_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x01FA](#cyble_evt_udsc_error_response) | [CYBLE_EVT_UDSC_ERROR_RESPONSE](#cyble_evt_udsc_error_response) |
| [User Data Service Events](#user_data_service_events) | [0x01FB](#cyble_evt_wptss_notification_enabled) | [CYBLE_EVT_WPTSS_NOTIFICATION_ENABLED](#cyble_evt_wptss_notification_enabled) |
| [User Data Service Events](#user_data_service_events) | [0x01FC](#cyble_evt_wptss_notification_disabled) | [CYBLE_EVT_WPTSS_NOTIFICATION_DISABLED](#cyble_evt_wptss_notification_disabled) |
| [User Data Service Events](#user_data_service_events) | [0x01FD](#cyble_evt_wptss_indication_enabled) | [CYBLE_EVT_WPTSS_INDICATION_ENABLED](#cyble_evt_wptss_indication_enabled) |
| [User Data Service Events](#user_data_service_events) | [0x01FE](#cyble_evt_wptss_indication_disabled) | [CYBLE_EVT_WPTSS_INDICATION_DISABLED](#cyble_evt_wptss_indication_disabled) |
| [User Data Service Events](#user_data_service_events) | [0x01FF](#cyble_evt_wptss_indication_confirmed) | [CYBLE_EVT_WPTSS_INDICATION_CONFIRMED](#cyble_evt_wptss_indication_confirmed) |
| [User Data Service Events](#user_data_service_events) | [0x0200](#cyble_evt_wptss_write_char) | [CYBLE_EVT_WPTSS_WRITE_CHAR](#cyble_evt_wptss_write_char) |
| [User Data Service Events](#user_data_service_events) | [0x0201](#cyble_evt_wptsc_notification) | [CYBLE_EVT_WPTSC_NOTIFICATION](#cyble_evt_wptsc_notification) |
| [User Data Service Events](#user_data_service_events) | [0x0202](#cyble_evt_wptsc_indication) | [CYBLE_EVT_WPTSC_INDICATION](#cyble_evt_wptsc_indication) |
| [User Data Service Events](#user_data_service_events) | [0x0203](#cyble_evt_wptsc_write_char_response) | [CYBLE_EVT_WPTSC_WRITE_CHAR_RESPONSE](#cyble_evt_wptsc_write_char_response) |
| [User Data Service Events](#user_data_service_events) | [0x0204](#cyble_evt_wptsc_read_char_response) | [CYBLE_EVT_WPTSC_READ_CHAR_RESPONSE](#cyble_evt_wptsc_read_char_response) |
| [User Data Service Events](#user_data_service_events) | [0x0205](#cyble_evt_wptsc_read_descr_response) | [CYBLE_EVT_WPTSC_READ_DESCR_RESPONSE](#cyble_evt_wptsc_read_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x0206](#cyble_evt_wptsc_write_descr_response) | [CYBLE_EVT_WPTSC_WRITE_DESCR_RESPONSE](#cyble_evt_wptsc_write_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x0207](#cyble_evt_wsss_indication_enabled) | [CYBLE_EVT_WSSS_INDICATION_ENABLED](#cyble_evt_wsss_indication_enabled) |
| [User Data Service Events](#user_data_service_events) | [0x0208](#cyble_evt_wsss_indication_disabled) | [CYBLE_EVT_WSSS_INDICATION_DISABLED](#cyble_evt_wsss_indication_disabled) |
| [User Data Service Events](#user_data_service_events) | [0x0209](#cyble_evt_wsss_indication_confirmed) | [CYBLE_EVT_WSSS_INDICATION_CONFIRMED](#cyble_evt_wsss_indication_confirmed) |
| [User Data Service Events](#user_data_service_events) | [0x020A](#cyble_evt_wssc_indication) | [CYBLE_EVT_WSSC_INDICATION](#cyble_evt_wssc_indication) |
| [User Data Service Events](#user_data_service_events) | [0x020B](#cyble_evt_wssc_read_char_response) | [CYBLE_EVT_WSSC_READ_CHAR_RESPONSE](#cyble_evt_wssc_read_char_response) |
| [User Data Service Events](#user_data_service_events) | [0x020C](#cyble_evt_wssc_read_descr_response) | [CYBLE_EVT_WSSC_READ_DESCR_RESPONSE](#cyble_evt_wssc_read_descr_response) |
| [User Data Service Events](#user_data_service_events) | [0x020D](#cyble_evt_wssc_write_descr_response) | [CYBLE_EVT_WSSC_WRITE_DESCR_RESPONSE](#cyble_evt_wssc_write_descr_response) |
| [Debug Events](#debug_events) | [0xE000](#cyble_debug_evt_bless_int) | [CYBLE_DEBUG_EVT_BLESS_INT](#cyble_debug_evt_bless_int) |
### Generic Events

#### CYBLE_EVT_HOST_INVALID
This event is triggered by BLE stack when stack is in a bad state, restarting stack is the only way to get out
of the state.

#### CYBLE_EVT_STACK_ON
This event is received when BLE stack is initialized and turned ON by invoking CyBle_StackInit () function.

#### CYBLE_EVT_TIMEOUT
This event is received when there is a timeout and application needs to handle the event. Timeout reason is
defined by [CYBLE_TO_REASON_CODE_T](#cyble_to_reason_code_t).

#### CYBLE_EVT_HARDWARE_ERROR
This event indicates that some internal hardware error has occurred. Reset of the hardware may be required.

#### CYBLE_EVT_HCI_STATUS
This event is triggered by 'Host Stack' if 'Controller' responds with an error code for any HCI command.
Event parameter returned will be an HCI error code as defined in Bluetooth 4.1 core specification, Volume 2,
Part D, section 1.3. This event will be received only if there is an error.

#### CYBLE_EVT_STACK_BUSY_STATUS
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
    and sufficient buffers are available to process application initiated transactions.
    The 'CYBLE_EVT_STACK_BUSY_STATUS' event with 'CYBLE_STACK_STATE_FREE' is indicated to 
    application if BLE Stack's internal buffer state has transitioned from 'CYBLE_STACK_STATE_BUSY'
    to 'CYBLE_STACK_STATE_FREE'.

To increase BLE stack's internal buffers count and achieve better throughput for attribute MTU greater then 32, 
use MaxAttrNoOfBuffer parameter in the Expression view of the Advanced tab.   

#### CYBLE_EVT_MEMORY_REQUEST
This event is received when stack wants application to provide memory to process remote request.

Event parameter is of type CYBLE_MEMORY_REQUEST_T.

This event is automatically handled by the component for the CYBLE_PREPARED_WRITE_REQUEST request. 
The component allocates sufficient memory for the long write request with assumption that attribute MTU size 
is negotiated to the minimum possible value. Application could use dynamic memory allocation to save static 
RAM memory consumption. To enable this event for application level, set EnableExternalPrepWriteBuff parameter
in the Expression view of the Advanced tab to the true.

#### CYBLE_EVT_MAX
Maximum value of CYBLE_EVENT_T type

### GAP Events
0x20 to 0x3F

#### CYBLE_EVT_GAPC_SCAN_PROGRESS_RESULT
This event is triggered every time a device is discovered; pointer to structure of type CYBLE_GAPC_ADV_REPORT_T 
is returned as the event parameter.

#### CYBLE_EVT_GAP_AUTH_REQ
This event is received by Peripheral and Central devices. When it is received by Peripheral, peripheral 
needs to Call CyBle_GappAuthReqReply() to reply to authentication request from Central.

When this event is received by Central, that means the slave has requested Central to initiate authentication
procedure. Central needs to call CyBle_GappAuthReq() to initiate authentication procedure.
Pointer to structure of type CYBLE_GAP_AUTH_INFO_T is returned as the event parameter.

#### CYBLE_EVT_GAP_PASSKEY_ENTRY_REQUEST
This event indicates that the device has to send passkey to be used during the pairing procedure. 
CyBle_GapAuthPassKeyReply() is required to be called with valid parameters on receiving this event.

Refer to Bluetooth Core Spec. 4.1, Part H, Section 2.3.5.1 Selecting STK Generation Method.

Nothing is returned as part of the event parameter.

#### CYBLE_EVT_GAP_PASSKEY_DISPLAY_REQUEST
This event indicates that the device needs to display passkey during the pairing procedure.

Refer to Bluetooth Core Spec. 4.1, Part H, Section 2.3.5.1 Selecting STK Generation Method.

Pointer to data of type 'uint32' is returned as part of the event parameter. Passkey can
be any 6-decimal-digit value.

#### CYBLE_EVT_GAP_AUTH_COMPLETE
This event indicates that the authentication procedure has been completed.

The event parameter contains the security information as defined by CYBLE_GAP_AUTH_INFO_T.

This event is generated at the end of the following three operations:

* Authentication is initiated with a newly connected device

* Encryption is initiated with a connected device that is already bonded

* Re-Encryption is initiated with a connected device with link already encrypted

During encryption/re-encryption, the Encryption Information exchanged during the pairing process
is used to encrypt/re-encrypt the link. As this does not modify any of the authentication 
parameters with which the devices were paired, this event is generated with NULL event data
and the result of the encryption operation.

#### CYBLE_EVT_GAP_AUTH_FAILED
Authentication process failed between two devices. The return value of type 
[CYBLE_GAP_AUTH_FAILED_REASON_T](#cyble_gap_auth_failed_reason_t) indicates the reason for failure.

#### CYBLE_EVT_GAPP_ADVERTISEMENT_START_STOP
Peripheral device has started/stopped advertising. 
This event is generated after making a call to CyBle_GappEnterDiscoveryMode and 
CyBle_GappExitDiscoveryMode functions. The event parameter contains the status
which is of type 'uint8'.

If the data is '0x00', it indicates 'success'; Anything else indicates 'failure'.

#### CYBLE_EVT_GAP_DEVICE_CONNECTED
This event is generated at the GAP Peripheral end after connection is completed with peer Central device.
For GAP Central device, this event is generated as in acknowledgment of receiving this event successfully
by BLE Controller. Once connection is done, no more event is required but if fails to establish connection,
'CYBLE_EVT_GAP_DEVICE_DISCONNECTED' is passed to application. ' CYBLE_EVT_GAP_ENHANCE_CONN_COMPLETE'
event is triggered instead of 'CYBLE_EVT_GAP_DEVICE_CONNECTED', if Link Layer Privacy is enabled in component customizer.   

Event parameter is a pointer to a structure of type CYBLE_GAP_CONN_PARAM_UPDATED_IN_CONTROLLER_T.

#### CYBLE_EVT_GAP_DEVICE_DISCONNECTED
Disconnected from remote device or failed to establish connection. Parameter returned with the event 
contains pointer to the reason for disconnection, which is of type uint8. For details refer
core spec 4.2, vol2, part D.

#### CYBLE_EVT_GAP_ENCRYPT_CHANGE
Encryption change event for active connection. 'evParam' can be decoded as

* evParam[0] = 0x00 -> Encryption OFF
* evParam[0] = 0x01 -> Encryption ON
* Any other value of evParam[0] -> Error

This is an informative event for application when there is a change in encryption. 

Application may choose to ignore it.

#### CYBLE_EVT_GAP_CONNECTION_UPDATE_COMPLETE
This event is generated at the GAP Central and the Peripheral end after connection parameter update
is requested from the host to the controller. Event parameter is a pointer to a structure of
type CYBLE_GAP_CONN_PARAM_UPDATED_IN_CONTROLLER_T.
        
#### CYBLE_EVT_GAPC_SCAN_START_STOP
Central device has started/stopped scanning. 

This event is generated after making a call to CyBle_GapcStartDiscovery and 
CyBle_GapcStopDiscovery APIs. The event parameter contains the status, which is of type 'uint8'.

If the data is '0x00', it indicates 'success'; Anything else indicates 'failure'.

#### CYBLE_EVT_GAP_KEYINFO_EXCHNGE_CMPLT
Indication that the SMP keys exchange with peer device is complete, the event handler
is expected to store the peer device keys, especially IRK which is used to resolve the
peer device after the connection establishment.

Event parameter returns data of type CYBLE_GAP_SMP_KEY_DIST_T containing the peer device keys.

#### CYBLE_EVT_GAP_NUMERIC_COMPARISON_REQUEST
This event indicates that the device needs to display passkey during 
secure connection pairing procedure. CyBle_GapAuthPassKeyReply() is
required to be called with valid parameters on receiving this event.
Since no key to be entered by the user for Numeric comparison, 
parameter passkey for the function CyBle_GapAuthPassKeyReply will be 
ignored.

Event parameter is a pointer to a 6 digit Passkey value.

#### CYBLE_EVT_GAP_KEYPRESS_NOTIFICATION
This event is generated when keypress (Secure connections) is received
from peer device.

#### CYBLE_EVT_GAP_OOB_GENERATED_NOTIFICATION
This event is generated when OOB generation for Secure connections is complete.  

Event parameter is of type 'CYBLE_GAP_OOB_DATA_T'

#### CYBLE_EVT_GAP_DATA_LENGTH_CHANGE
The LE Data Length Change event notifies the Host of a change to either the maximum Payload length or 
the maximum transmission time of Data Channel PDUs in either direction. The values reported are the maximum
that will actually be used on the connection following the change. Event parameter is of type 
'CYBLE_GAP_CONN_DATA_LENGTH_T'

#### CYBLE_EVT_GAP_ENHANCE_CONN_COMPLETE
The LE Enhanced Connection Complete event indicates application that a new connection has been created when 
Link Layer Privacy is enabled in component customizer. 

Event parameter is of type 'CYBLE_GAP_ENHANCE_CONN_COMPLETE_T'

#### CYBLE_EVT_GAPC_DIRECT_ADV_REPORT
The LE Direct Advertising Report event indicates that directed advertisements have been received where 
the advertiser is using a resolvable private address for the InitA field in the ADV_DIRECT_IND PDU and the
Scanning_Filter_Policy is equal to 0x02 or 0x03. Event parameter is of type 'CYBLE_GAPC_DIRECT_ADV_REPORT_T'

#### CYBLE_EVT_GAP_SMP_NEGOTIATED_AUTH_INFO
SMP negotiated auth info event is raised as soon as SMP has completed pairing properties (feature exchange)
negotiation. The event parameter is CYBLE_GAP_AUTH_INFO_T. CYBLE_GAP_AUTH_INFO_T will have the 
negotiated parameter, the pairing should either pass with these negotiated parameters or may fail. This event
is applicable to both GAP Central and GAP Peripheral devices. In GAP Peripheral, this event is called from 
API-CyBle_GappAuthReqReply context.

### GATT Events
0x40 to 0x6F

#### CYBLE_EVT_GATTC_ERROR_RSP
The event is received by the Client when the Server cannot perform the requested 
operation and sends out an error response. Event parameter is a pointer to a structure
of type CYBLE_GATTC_ERR_RSP_PARAM_T.

#### CYBLE_EVT_GATT_CONNECT_IND
This event is generated at the GAP Peripheral end after connection is completed with peer Central device.
For GAP Central device, this event is generated as in acknowledgment of receiving this event successfully
by BLE Controller. Once connection is done, no more event is required but if fails to establish connection,
'CYBLE_EVT_GATT_DISCONNECT_IND' is passed to application.

Event parameter is a pointer to a structure of type CYBLE_CONN_HANDLE_T.

#### CYBLE_EVT_GATT_DISCONNECT_IND
GATT is disconnected. Nothing is returned as part of the event parameter.

#### CYBLE_EVT_GATTS_XCNHG_MTU_REQ
'GATT MTU Exchange Request' received from GATT client device. Event parameter 
contains the MTU size of type CYBLE_GATT_XCHG_MTU_PARAM_T.

#### CYBLE_EVT_GATTC_XCHNG_MTU_RSP
'GATT MTU Exchange Response' received from server device. Event parameter is a
pointer to a structure of type CYBLE_GATT_XCHG_MTU_PARAM_T.

#### CYBLE_EVT_GATTC_READ_BY_GROUP_TYPE_RSP
'Read by Group Type Response' received from server device. Event parameter
is a pointer to a structure of type CYBLE_GATTC_READ_BY_GRP_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_READ_BY_TYPE_RSP
'Read by Type Response' received from server device. Event parameter is a
pointer to a structure of type CYBLE_GATTC_READ_BY_TYPE_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_FIND_INFO_RSP
'Find Information Response' received from server device. Event parameter is
a pointer to a structure of type 'CYBLE_GATTC_FIND_INFO_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_FIND_BY_TYPE_VALUE_RSP
'Find by Type Value Response' received from server device. Event parameter is
a pointer to a structure of type CYBLE_GATTC_FIND_BY_TYPE_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_READ_RSP
'Read Response' from server device. Event parameter is a pointer to a
structure of type CYBLE_GATTC_READ_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_READ_BLOB_RSP
'Read Blob Response' from server. Event parameter is a pointer to a
structure of type CYBLE_GATTC_READ_RSP_PARAM_T.

#### CYBLE_EVT_GATTC_READ_MULTI_RSP
'Read Multiple Responses' from server. Event parameter is a pointer
to a structure of type CYBLE_GATTC_READ_RSP_PARAM_T. The 'actualLen' field
should be ignored as it is unused in this event response.

#### CYBLE_EVT_GATTS_WRITE_REQ
'Write Request' from client device. Event parameter is a pointer to
a structure of type CYBLE_GATTS_WRITE_REQ_PARAM_T.

#### CYBLE_EVT_GATTC_WRITE_RSP
'Write Response' from server device. Event parameter is a pointer
to a structure of type CYBLE_CONN_HANDLE_T.

#### CYBLE_EVT_GATTS_WRITE_CMD_REQ
'Write Command' Request from client device. Event parameter is a 
pointer to a structure of type CYBLE_GATTS_WRITE_CMD_REQ_PARAM_T.

#### CYBLE_EVT_GATTS_PREP_WRITE_REQ
'Prepare Write' Request from client device. Event parameter is a
pointer to a structure of type CYBLE_GATTS_PREP_WRITE_REQ_PARAM_T.

#### CYBLE_EVT_GATTS_EXEC_WRITE_REQ
'Execute Write' request from client device. Event parameter is a
pointer to a structure of type 'CYBLE_GATTS_EXEC_WRITE_REQ_T'
This event will be triggered before GATT DB is modified. GATT Db will be updated 
only if there is no error condition provided by application. In case of error condition triggered
during stack validation, partial write will occur. Write will be canceled from that handle where 
error has occurred and error response corresponding to that handle will be sent to remote.
If at any point of time 'CYBLE_GATT_EXECUTE_WRITE_CANCEL_FLAG' is received in 
execWriteFlag fields of 'CYBLE_GATTS_EXEC_WRITE_REQ_T' structure, then all previous 
writes are canceled. For execute cancel scenario, all elements of 
'CYBLE_GATTS_EXEC_WRITE_REQ_T' should be ignored except execWriteFlag and connHandle.

#### CYBLE_EVT_GATTC_EXEC_WRITE_RSP
'Execute Write' response from server device. Event parameter is a
pointer to a structure of type CYBLE_GATTC_EXEC_WRITE_RSP_T.

#### CYBLE_EVT_GATTC_HANDLE_VALUE_NTF
Notification data received from server device. Event parameter
is a pointer to a structure of type CYBLE_GATTC_HANDLE_VALUE_NTF_PARAM_T.

#### CYBLE_EVT_GATTC_HANDLE_VALUE_IND
Indication data received from server device. Event parameter is
a pointer to a structure of type CYBLE_GATTC_HANDLE_VALUE_IND_PARAM_T.

#### CYBLE_EVT_GATTS_HANDLE_VALUE_CNF
Confirmation to indication response from client device. Event
parameter is a pointer to a structure of type CYBLE_CONN_HANDLE_T.

#### CYBLE_EVT_GATTS_DATA_SIGNED_CMD_REQ
Confirmation to indication response from client device. Event
parameter is a pointer to a structure of type CYBLE_GATTS_SIGNED_WRITE_CMD_REQ_PARAM_T. 
if value.val parameter is set to Zero, then signature is not matched and ignored by stack.

#### CYBLE_EVT_GATTC_STOP_CMD_COMPLETE
Event indicating that GATT group procedure has stopped or completed, this event occurs
only if application has called CyBle_GattcStopCmd API. 

Event parameters shall be ignored.

#### CYBLE_EVT_GATTS_READ_CHAR_VAL_ACCESS_REQ
Event parameter type is CYBLE_GATTS_CHAR_VAL_READ_REQ_T. It is triggered on server side 
when client sends read request and when characteristic has CYBLE_GATT_DB_ATTR_CHAR_VAL_RD_EVENT 
property set. This event could be ignored by application unless it need to response by error response which
needs to be set in gattErrorCode field of event parameter.

#### CYBLE_EVT_GATTC_LONG_PROCEDURE_END
Event indicates that GATT long procedure is end and stack will not send any further
requests to peer. Either this event or 'CYBLE_EVT_GATTC_ERROR_RSP' will be received
by application. This event may get triggered for below GATT long procedures:

1. CyBle_GattcDiscoverAllPrimaryServices
1. CyBle_GattcDiscoverPrimaryServiceByUuid
1. CyBle_GattcFindIncludedServices
1. CyBle_GattcDiscoverAllCharacteristics
1. CyBle_GattcDiscoverCharacteristicByUuid
1. CyBle_GattcDiscoverAllCharacteristicDescriptors
1. CyBle_GattcReadLongCharacteristicValues
1. CyBle_GattcReadLongCharacteristicDescriptors

Event parameter is ATT opcode for the corresponding long GATT Procedure.

### L2CAP Events
0x70 to 0x7F

#### CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_REQ
This event indicates the connection parameter update received
from the remote device. The application is expected to reply to L2CAP using the
CyBle_L2capLeConnectionParamUpdateResponse() function to respond to the remote
device, whether parameters are accepted or rejected.

#### CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_RSP
This event indicates the connection parameter update response received
from the master. Event Parameter pointer points to data with two possible values:

* Accepted = 0x0000
* Rejected  = 0x0001

Data is of type unit16.

#### CYBLE_EVT_L2CAP_COMMAND_REJ
This event indicates that the request send over l2cap signaling has been
rejected. Event parameter is a pointer to a structure of type
CYBLE_L2CAP_COMMAND_REJ_REASON_T.

#### CYBLE_EVT_L2CAP_CBFC_CONN_IND
This event is used to inform application of the incoming L2CAP CBFC
Connection Request. Event parameter is a pointer to a structure of type
CYBLE_L2CAP_CBFC_CONN_IND_PARAM_T is returned.

#### CYBLE_EVT_L2CAP_CBFC_CONN_CNF
This event is used to inform application of the L2CAP CBFC Connection
Response/Confirmation. Event parameter is a pointer to a structure of
type CYBLE_L2CAP_CBFC_CONN_CNF_PARAM_T is returned.

#### CYBLE_EVT_L2CAP_CBFC_DISCONN_IND
This event is used to inform application of the L2CAP CBFC Disconnection
Request received from the Peer device. Event parameter is a pointer to
Local CID of type unit16.

#### CYBLE_EVT_L2CAP_CBFC_DISCONN_CNF
This event is used to inform application of the L2CAP CBFC Disconnection
confirmation/Response received from the Peer device. Event parameter is a
pointer to a structure of type CYBLE_L2CAP_CBFC_DISCONN_CNF_PARAM_T.

#### CYBLE_EVT_L2CAP_CBFC_DATA_READ
This event is used to inform application of data received over L2CAP
CBFC channel. Event parameter is a pointer to a structure of type
CYBLE_L2CAP_CBFC_RX_PARAM_T.

#### CYBLE_EVT_L2CAP_CBFC_RX_CREDIT_IND
This event is used to inform the application of receive credits reached
low mark. After receiving L2CAP data/payload from peer device for a
specification Channel, the available credits are calculated.

If the credit count goes below the low mark, this event is called to inform
the application of the condition, so that if the application wants it can
send more credits to the peer device.

Event parameter is a pointer to a structure of type
CYBLE_L2CAP_CBFC_LOW_RX_CREDIT_PARAM_T.

#### CYBLE_EVT_L2CAP_CBFC_TX_CREDIT_IND
This event is used to inform application of having received transmit
credits. This event is called on receiving LE Flow Control Credit from peer
device.

Event parameter is a pointer to a structure of type
CYBLE_L2CAP_CBFC_LOW_TX_CREDIT_PARAM_T.

If the 'result' field of the received data is non-zero, this indicates an
error. If the sum of 'credit' field value and the previously available credit
at the peer device receiving credit information exceeds 65535, it indicates a
'credit overflow' error.

In case of error, the peer device receiving this event should initiate
disconnection of the L2CAP channel by invoking CyBle_L2capDisconnectReq () 
function.

#### CYBLE_EVT_L2CAP_CBFC_DATA_WRITE_IND
This event is used to inform application of data transmission completion over L2CAP CBFC
channel. Event parameter is of type 'CYBLE_L2CAP_CBFC_DATA_WRITE_PARAM_T' 
This event will be deprecated in future. It is only kept for backward compatibility.
It is not recommended to be used by new design.

### Host Qualification Events
0x80 to 0x8F

Normally not defined.

#### CYBLE_EVT_QUAL_SMP_PAIRING_REQ_RSP
Tester to manipulate pairing request or response PDU. Event parameter is a pointer to 1 bytes data.
Tester can manipulate the bits of the byte.

#### CYBLE_EVT_QUAL_SMP_LOCAL_PUBLIC_KEY
Tester to manipulate local Public Key. Event parameter is a pointer to local public key of size 64 Bytes.
Tester can manipulate the bits/bytes.

#### CYBLE_EVT_QUAL_SMP_PAIRING_FAILED_CMD
Tester to assign pairing failed error code. Event parameter is a pointer to 16 bits value.
Tester should assign error code to lower bits.

### Future Use Events
0x90 to 0xFE

#### CYBLE_EVT_PENDING_FLASH_WRITE
This event is used to inform application that flash write is pending
stack internal data structures are modified and require backup.

#### CYBLE_EVT_LE_PING_AUTH_TIMEOUT
LE PING Authentication Timeout Event to indicate that peer device has not responded
with the valid MIC packet within the application configured ping authentication time.

### GATT Service Events

#### CYBLE_EVT_GATTS_INDICATION_ENABLED
GATT Server - Indications for GATT Service's "Service Changed"
Characteristic were enabled. The parameter of this event is a structure of
CYBLE_GATTS_WRITE_REQ_PARAM_T type.

#### CYBLE_EVT_GATTS_INDICATION_DISABLED
GATT Server - Indications for GATT Service's "Service Changed"
Characteristic were disabled. The parameter of this event is a structure of
CYBLE_GATTS_WRITE_REQ_PARAM_T type.

#### CYBLE_EVT_GATTC_INDICATION
GATT Client - GATT Service's "Service Changed" Characteristic Indications 
were received. The parameter of this event is a structure
of CYBLE_GATTC_HANDLE_VALUE_IND_PARAM_T type.

### Service Discovery Events

#### CYBLE_EVT_GATTC_SRVC_DISCOVERY_FAILED
GATT Client - Service discovery procedure failed. This event may
be generated on calling CyBle_GattcDiscoverAllPrimaryServices().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_INCL_DISCOVERY_FAILED
GATT Client - Discovery of included services failed. This event may
be generated on calling CyBle_GattcFindIncludedServices().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_CHAR_DISCOVERY_FAILED
GATT Client - Discovery of service's characteristics failed. This event may
be generated on calling CyBle_GattcDiscoverAllCharacteristics() or
CyBle_GattcReadUsingCharacteristicUuid(). 
No parameters passed for this event.

#### CYBLE_EVT_GATTC_DESCR_DISCOVERY_FAILED
GATT Client - Discovery of service's characteristics failed. This event may
be generated on calling CyBle_GattcDiscoverAllCharacteristicDescriptors().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_SRVC_DUPLICATION
GATT Client - Duplicate service record was found during server device
discovery. The parameter of this event is a structure of uint16 (UUID16)
type.

#### CYBLE_EVT_GATTC_CHAR_DUPLICATION
GATT Client - Duplicate service's characteristic record was found during 
server device discovery. The parameter of this event is a structure
of uint16 (UUID16) type.

#### CYBLE_EVT_GATTC_DESCR_DUPLICATION
GATT Client - Duplicate service's characteristic descriptor record was found
during server device discovery. The parameter of this event is a structure
of uint16 (UUID16) type.

#### CYBLE_EVT_GATTC_SRVC_DISCOVERY_COMPLETE
GATT Client - Service discovery procedure completed successfully. This
event may be generated on calling CyBle_GattcDiscoverAllPrimaryServices().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_INCL_DISCOVERY_COMPLETE
GATT Client - Included services discovery is completed
successfully. This event may be generated on calling
CyBle_GattcFindIncludedServices().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_CHAR_DISCOVERY_COMPLETE
GATT Client - Discovery of service's characteristics discovery is completed
successfully. This event may be generated on calling
CyBle_GattcDiscoverAllCharacteristics() or
CyBle_GattcReadUsingCharacteristicUuid().
No parameters passed for this event.

#### CYBLE_EVT_GATTC_DISCOVERY_COMPLETE
GATT Client - Discovery of remote device completed successfully.
No parameters passed for this event.

### ANCS Service Events

#### CYBLE_EVT_ANCSS_NOTIFICATION_ENABLED
ANCS Server - Notifications for Apple Notification Center Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSS_NOTIFICATION_DISABLED
ANCS Server - Notifications for Apple Notification Center Service Characteristic
were disabled. The parameter of this event is a structure of
CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSS_WRITE_CHAR
ANCS Server - Write Request for Apple Notification Center Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSC_NOTIFICATION
ANCS Client - Apple Notification Center Characteristic Service Notification 
was received. The parameter of this event is a structure
of CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSC_READ_CHAR_RESPONSE
ANCS Client - Read Response for Apple Notification Center Service Characteristic
Value. The parameter of this event is a structure of 
CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSC_WRITE_CHAR_RESPONSE
ANCS Client - Write Response for Write Request for Apple Notification Center Service
Characteristic Value. The parameter of this event is a structure of 
CYBLE_ANCS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANCSC_READ_DESCR_RESPONSE
ANCS Client - Read Response for Read Request for Apple Notification Center Service
Characteristic Descriptor Read Request. The parameter of this event is a
structure of CYBLE_ANCS_DESCR_VALUE_T type.

#### CYBLE_EVT_ANCSC_WRITE_DESCR_RESPONSE
ANCS Client - Write Response for Write Request for Apple Notification Center Service
Client Characteristic Configuration Descriptor Value. The parameter of
this event is a structure of CYBLE_ANCS_DESCR_VALUE_T type.

#### CYBLE_EVT_ANCSC_ERROR_RESPONSE
ANCS Client - Error Response for Write Request for Apple Notification Center Service
Characteristic Value. The parameter of this event is a structure of 
CYBLE_ANCS_CHAR_VALUE_T type.

### ANS Service Events

#### CYBLE_EVT_ANSS_NOTIFICATION_ENABLED
ANS Server - Notifications for Alert Notification Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSS_NOTIFICATION_DISABLED
ANS Server - Notifications for Alert Notification Service Characteristic
were disabled. The parameter of this event is a structure of
CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSS_CHAR_WRITE
ANS Server - Write Request for Alert Notification Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSC_NOTIFICATION
ANS Client - Alert Notification Characteristic Service Notification 
was received. The parameter of this event is a structure
of CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSC_READ_CHAR_RESPONSE
ANS Client - Read Response for Alert Notification Service Characteristic
Value. The parameter of this event is a structure of 
CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSC_WRITE_CHAR_RESPONSE
ANS Client - Write Response for Write Request for Alert Notification Service
Characteristic Value. The parameter of this event is a structure of 
CYBLE_ANS_CHAR_VALUE_T type.

#### CYBLE_EVT_ANSC_READ_DESCR_RESPONSE
ANS Client - Read Response for Read Request for Alert Notification Service
Characteristic Descriptor Read Request. The parameter of this event is a
structure of CYBLE_ANS_DESCR_VALUE_T type.

#### CYBLE_EVT_ANSC_WRITE_DESCR_RESPONSE
ANS Client - Write Response for Write Request for Alert Notification Service
Client Characteristic Configuration Descriptor Value. The parameter of
this event is a structure of CYBLE_ANS_DESCR_VALUE_T type.

### BAS Service Events

#### CYBLE_EVT_BASS_NOTIFICATION_ENABLED
BAS Server - Notifications for Battery Level Characteristic were enabled. The
parameter of this event is a structure of CYBLE_BAS_CHAR_VALUE_T type.

#### CYBLE_EVT_BASS_NOTIFICATION_DISABLED
BAS Server - Notifications for Battery Level Characteristic were disabled. The
parameter of this event is a structure of CYBLE_BAS_CHAR_VALUE_T type.

#### CYBLE_EVT_BASC_NOTIFICATION
BAS Client - Battery Level Characteristic Notification was received. The 
parameter of this event is a structure of CYBLE_BAS_CHAR_VALUE_T type.

#### CYBLE_EVT_BASC_READ_CHAR_RESPONSE
BAS Client - Read Response for Battery Level Characteristic Value. The 
parameter of this event is a structure of CYBLE_BAS_CHAR_VALUE_T type.

#### CYBLE_EVT_BASC_READ_DESCR_RESPONSE
BAS Client - Read Response for Battery Level Characteristic Descriptor Read 
Request. The parameter of this event is a structure of 
CYBLE_BAS_DESCR_VALUE_T type.

#### CYBLE_EVT_BASC_WRITE_DESCR_RESPONSE
BAS Client - Write Response for Battery Level Client Characteristic 
Configuration Descriptor Value. The parameter of this event is a structure of 
CYBLE_BAS_DESCR_VALUE_T type.

### Body Composition Service Events

#### CYBLE_EVT_BCSS_INDICATION_ENABLED
BCS Server - Indication for Body Composition Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_BCS_CHAR_VALUE_T type.

#### CYBLE_EVT_BCSS_INDICATION_DISABLED
BCS Server - Indication for Body Composition Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_BCS_CHAR_VALUE_T type.

#### CYBLE_EVT_BCSS_INDICATION_CONFIRMED
BCS Server - Body Composition Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_BCS_CHAR_VALUE_T type.

#### CYBLE_EVT_BCSC_INDICATION
BCS Client - Body Composition Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_BCS_CHAR_VALUE_T type.

#### CYBLE_EVT_BCSC_READ_CHAR_RESPONSE
BCS Client - Read Response for Read Request of Body Composition 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_BCS_CHAR_VALUE_T type.

#### CYBLE_EVT_BCSC_READ_DESCR_RESPONSE
BCS Client - Read Response for Read Request of Body Composition
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_BCS_DESCR_VALUE_T type.

#### CYBLE_EVT_BCSC_WRITE_DESCR_RESPONSE
BCS Client - Write Response for Write Request of Body Composition
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_BCS_DESCR_VALUE_T type.

### Blood Pressure Service Events

#### CYBLE_EVT_BLSS_INDICATION_ENABLED
BLS Server - Indication for Blood Pressure Service Characteristic was enabled.
The parameter of this event is a structure of CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSS_INDICATION_DISABLED
BLS Server - Indication for Blood Pressure Service Characteristic was 
disabled. The parameter of this event is a structure of 
CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSS_INDICATION_CONFIRMED
BLS Server - Blood Pressure Service Characteristic Indication was confirmed.
The parameter of this event is a structure of CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSS_NOTIFICATION_ENABLED
BLS Server - Notifications for Blood Pressure Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_BLS_CHAR_VALUE_T type.

#### CYBLE_EVT_BLSS_NOTIFICATION_DISABLED
BLS Server - Notifications for Blood Pressure Service Characteristic
were disabled. The parameter of this event is a structure of
CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSC_INDICATION
BLS Client - Blood Pressure Service Characteristic Indication was received. 
The parameter of this event is a structure of CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSC_NOTIFICATION
BLS Client - Blood Pressure Service Characteristic Notification was received.
The parameter of this event is a structure of CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSC_READ_CHAR_RESPONSE
BLS Client - Read Response for Read Request of Blood Pressure Service 
Characteristic value. The parameter of this event is a structure of
CYBLE_BLS_CHAR_VALUE_T type

#### CYBLE_EVT_BLSC_READ_DESCR_RESPONSE
BLS Client - Read Response for Read Request of Blood Pressure Service 
Characteristic Descriptor Read request. The parameter of this event is a
structure of CYBLE_BLS_DESCR_VALUE_T type

#### CYBLE_EVT_BLSC_WRITE_DESCR_RESPONSE
BLS Client - Write Response for Write Request of Blood Pressure Service
Characteristic Configuration Descriptor value. The parameter of this event
is a structure of CYBLE_BLS_DESCR_VALUE_T type

### Bond Management Service Events

#### CYBLE_EVT_BMSS_WRITE_CHAR
BMS Server - Write Request for Bond Management
was received. The parameter of this event is a structure
of CYBLE_BMS_CHAR_VALUE_T type.

#### CYBLE_EVT_BMSC_READ_CHAR_RESPONSE
BMS Client - Read Response for Read Request of Bond Management Service 
Characteristic value. The parameter of this event is a structure of
CYBLE_BMS_CHAR_VALUE_T type

#### CYBLE_EVT_BMSC_WRITE_CHAR_RESPONSE
BMS Client - Write Response for Write Request of Bond Management
Service Characteristic value. The 
parameter of this event is a structure of
CYBLE_BMS_CHAR_VALUE_T type.

#### CYBLE_EVT_BMSC_READ_DESCR_RESPONSE
BMS Client - Read Response for Read Request of Bond Management Service 
Characteristic Descriptor Read request. The parameter of this event is a
structure of CYBLE_BMS_DESCR_VALUE_T type.

### CGM Service Events

#### CYBLE_EVT_CGMSS_INDICATION_ENABLED
CGMS Server - Indication for Continuous Glucose Monitoring Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSS_INDICATION_DISABLED
CGMS Server - Indication for Continuous Glucose Monitoring Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSS_INDICATION_CONFIRMED
CGMS Server - Continuous Glucose Monitoring Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSS_NOTIFICATION_ENABLED
CGMS Server - Notifications for Continuous Glucose Monitoring Service Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSS_NOTIFICATION_DISABLED
CGMS Server - Notifications for Continuous Glucose Monitoring Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSS_WRITE_CHAR
CGMS Server - Write Request for Continuous Glucose Monitoring Service 
was received. The parameter of this event is a structure
of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSC_INDICATION
CGMS Client - Continuous Glucose Monitoring Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSC_NOTIFICATION
CGMS Client - Continuous Glucose Monitoring Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSC_READ_CHAR_RESPONSE
CGMS Client - Read Response for Read Request of Continuous Glucose Monitoring 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSC_WRITE_CHAR_RESPONSE
CGMS Client - Write Response for Write Request of Continuous Glucose Monitoring
Service Characteristic value. The 
parameter of this event is a structure of
CYBLE_CGMS_CHAR_VALUE_T type.

#### CYBLE_EVT_CGMSC_READ_DESCR_RESPONSE
CGMS Client - Read Response for Read Request of Continuous Glucose Monitoring
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_CGMS_DESCR_VALUE_T type.

#### CYBLE_EVT_CGMSC_WRITE_DESCR_RESPONSE
CGMS Client - Write Response for Write Request of Continuous Glucose Monitoring
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_CGMS_DESCR_VALUE_T type.

### CPS Service Events

#### CYBLE_EVT_CPSS_NOTIFICATION_ENABLED
CPS Server - Notifications for Cycling Power Service Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_CPS_CHAR_VALUE_T type.

#### CYBLE_EVT_CPSS_NOTIFICATION_DISABLED
CPS Server - Notifications for Cycling Power Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_INDICATION_ENABLED
CPS Server - Indication for Cycling Power Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_INDICATION_DISABLED
CPS Server - Indication for Cycling Power Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_INDICATION_CONFIRMED
CPS Server - Cycling Power Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_BROADCAST_ENABLED
CPS Server - Broadcast for Cycling Power Service Characteristic
was enabled. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_BROADCAST_DISABLED
CPS Server - Broadcast for Cycling Power Service Characteristic
was disabled. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSS_CHAR_WRITE
CPS Server - Write Request for Cycling Power Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_CPS_CHAR_VALUE_T type.

#### CYBLE_EVT_CPSC_NOTIFICATION
CPS Client - Cycling Power Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSC_INDICATION
CPS Client - Cycling Power Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSC_READ_CHAR_RESPONSE
CPS Client - Read Response for Read Request of Cycling Power Service
Characteristic value. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type

#### CYBLE_EVT_CPSC_WRITE_CHAR_RESPONSE
CPS Client - Write Response for Write Request of Cycling Power Service
Characteristic value. The parameter of this event
is a structure of CYBLE_CPS_CHAR_VALUE_T type.

#### CYBLE_EVT_CPSC_READ_DESCR_RESPONSE
CPS Client - Read Response for Read Request of Cycling Power
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_CPS_DESCR_VALUE_T type.

#### CYBLE_EVT_CPSC_WRITE_DESCR_RESPONSE
CPS Client - Write Response for Write Request of Cycling Power
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_CPS_DESCR_VALUE_T type.

#### CYBLE_EVT_CPSC_SCAN_PROGRESS_RESULT
CPS Client - This event is triggered every time a device receive
non-connectable undirected advertising event.
The parameter of this event is a structure of 
CYBLE_CPS_CHAR_VALUE_T type.

### Cycling Speed and Cadence Service Events

#### CYBLE_EVT_CSCSS_NOTIFICATION_ENABLED
CSCS Server - Notifications for Cycling Speed and Cadence Service
Characteristic were enabled. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSS_NOTIFICATION_DISABLED
CSCS Server - Notifications for Cycling Speed and Cadence Service
Characteristic were disabled. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSS_INDICATION_ENABLED
CSCS Server - Indication for Cycling Speed and Cadence Service Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSS_INDICATION_DISABLED
CSCS Server - Indication for Cycling Speed and Cadence Service Characteristic
was disabled. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSS_INDICATION_CONFIRMATION
CSCS Server - Cycling Speed and Cadence Service Characteristic
Indication was confirmed. The parameter of this event is a structure of 
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSS_CHAR_WRITE
CSCS Server - Write Request for Cycling Speed and Cadence Service
Characteristic was received. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSC_NOTIFICATION
CSCS Client - Cycling Speed and Cadence Service Characteristic
Notification was received. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSC_INDICATION
CSCS Client - Cycling Speed and Cadence Service Characteristic
Indication was received. The parameter of this event is a structure of 
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSC_READ_CHAR_RESPONSE
CSCS Client - Read Response for Read Request of Cycling Speed and Cadence 
Service Characteristic value. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSC_WRITE_CHAR_RESPONSE
CSCS Client - Write Response for Write Request of Cycling Speed and Cadence 
Service Characteristic value. The parameter of this event is a structure of
CYBLE_CSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_CSCSC_READ_DESCR_RESPONSE
CSCS Client - Read Response for Read Request of Cycling Speed and Cadence
Service Characteristic Descriptor Read request. The parameter of this event
is a structure of CYBLE_CSCS_DESCR_VALUE_T type.

#### CYBLE_EVT_CSCSC_WRITE_DESCR_RESPONSE
CSCS Client - Write Response for Write Request of Cycling Speed and Cadence
Service Characteristic Configuration Descriptor value. The parameter of
this event is a structure of  CYBLE_CSCS_DESCR_VALUE_T type.

### Current Time Service Events

#### CYBLE_EVT_CTSS_NOTIFICATION_ENABLED
CTS Server - Notification for Current Time Characteristic was enabled. The
parameter of this event is a structure of CYBLE_CTS_CHAR_VALUE_T type.

#### CYBLE_EVT_CTSS_NOTIFICATION_DISABLED
CTS Server - Notification for Current Time Characteristic was disabled. The
parameter of this event is a structure of CYBLE_CTS_CHAR_VALUE_T type.

#### CYBLE_EVT_CTSS_CHAR_WRITE
CTS Server - Write Request for Current Time Service
Characteristic was received. The parameter of this event is a structure of
CYBLE_CTS_CHAR_VALUE_T type. When this event is received the user is 
responsible for performing any kind of data verification and writing the 
data to the GATT database in case of successful verification or setting
the error using CyBle_SetGattError() in case of data verification failure.

#### CYBLE_EVT_CTSC_NOTIFICATION
CTS Client - Current Time Characteristic Notification was received. The
parameter of this event is a structure of CYBLE_CTS_CHAR_VALUE_T type.

#### CYBLE_EVT_CTSC_READ_CHAR_RESPONSE
CTS Client - Read Response for Current Time Characteristic
Value Read Request. The parameter of this event is a 
structure of CYBLE_CTS_CHAR_VALUE_T type.

#### CYBLE_EVT_CTSC_READ_DESCR_RESPONSE
CTS Client - Read Response for Current Time Client
Characteristic Configuration Descriptor Value Read 
Request. The parameter of this event is a 
structure of CYBLE_CTS_DESCR_VALUE_T type.

#### CYBLE_EVT_CTSC_WRITE_DESCR_RESPONSE
CTS Client - Write Response for Current Time Characteristic
Configuration Descriptor Value. The parameter of this 
event is a structure of CYBLE_CTS_DESCR_VALUE_T type.

#### CYBLE_EVT_CTSC_WRITE_CHAR_RESPONSE
CTS Client - Write Response for Current Time or Local
Time Information Characteristic Value. The parameter of this
event is a structure of CYBLE_CTS_DESCR_VALUE_T type.

### DIS Service Events

#### CYBLE_EVT_DISC_READ_CHAR_RESPONSE
DIS Client - Read Response for a Read Request for a
Device Information Service Characteristic. The parameter of this 
event is a structure of CYBLE_DIS_CHAR_VALUE_T type.

### Environmental Sensing Service Events

#### CYBLE_EVT_ESSS_NOTIFICATION_ENABLED
ESS Server - Notifications for Environmental Sensing Service
Characteristic were enabled. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_NOTIFICATION_DISABLED
ESS Server - Notifications for Environmental Sensing Service
Characteristic were disabled. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_INDICATION_ENABLED
ESS Server - Indication for Environmental Sensing Service Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_INDICATION_DISABLED
ESS Server - Indication for Environmental Sensing Service Characteristic
was disabled. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_INDICATION_CONFIRMATION
ESS Server - Environmental Sensing Service Characteristic
Indication was confirmed. The parameter of this event is a structure of 
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_CHAR_WRITE
ESS Server - Write Request for Environmental Sensing Service
Characteristic was received. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSS_EXEC_WRITE_REQ
ESS Server - Execute Write Request for Environmental Sensing Service
Characteristic was received. The parameter of this event is a structure of
CYBLE_ESS_DESCR_VALUE_T type.

#### CYBLE_EVT_ESSS_DESCR_WRITE
ESS Server - Write Request for Environmental Sensing Service
Characteristic Descriptor was received. The parameter of this event is a structure of
CYBLE_ESS_DESCR_VALUE_T type. This event is generated only when write for
CYBLE_ESS_CHAR_USER_DESCRIPTION_DESCR, CYBLE_ESS_ES_TRIGGER_SETTINGS_DESCR or
CYBLE_ESS_ES_CONFIG_DESCR occurred.

#### CYBLE_EVT_ESSC_NOTIFICATION
ESS Client - Environmental Sensing Service Characteristic
Notification was received. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSC_INDICATION
ESS Client - Environmental Sensing Service Characteristic
Indication was received. The parameter of this event is a structure of 
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSC_READ_CHAR_RESPONSE
ESS Client - Read Response for Read Request of Environmental Sensing 
Service Characteristic value. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSC_WRITE_CHAR_RESPONSE
ESS Client - Write Response for Write Request of Environmental Sensing 
Service Characteristic value. The parameter of this event is a structure of
CYBLE_ESS_CHAR_VALUE_T type.

#### CYBLE_EVT_ESSC_READ_DESCR_RESPONSE
ESS Client - Read Response for Read Request of Environmental Sensing
Service Characteristic Descriptor Read request. The parameter of this event
is a structure of CYBLE_ESS_DESCR_VALUE_T type.

#### CYBLE_EVT_ESSC_WRITE_DESCR_RESPONSE
ESS Client - Write Response for Write Request of Environmental Sensing
Service Characteristic Configuration Descriptor value. The parameter of
this event is a structure of  CYBLE_ESS_DESCR_VALUE_T type.

### Glucose Service Events

#### CYBLE_EVT_GLSS_INDICATION_ENABLED
GLS Server - Indication for Glucose Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSS_INDICATION_DISABLED
GLS Server - Indication for Glucose Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSS_INDICATION_CONFIRMED
GLS Server - Glucose Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSS_NOTIFICATION_ENABLED
GLS Server - Notifications for Glucose Service Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSS_NOTIFICATION_DISABLED
GLS Server - Notifications for Glucose Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSS_WRITE_CHAR
GLS Server - Write Request for Glucose Service 
was received. The parameter of this event is a structure
of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSC_INDICATION
GLS Client - Glucose Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSC_NOTIFICATION
GLS Client - Glucose Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSC_READ_CHAR_RESPONSE
GLS Client - Read Response for Read Request of Glucose 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSC_WRITE_CHAR_RESPONSE
GLS Client - Write Response for Write Request of Glucose
Service Characteristic value. The 
parameter of this event is a structure of
CYBLE_GLS_CHAR_VALUE_T type.

#### CYBLE_EVT_GLSC_READ_DESCR_RESPONSE
GLS Client - Read Response for Read Request of Glucose
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_GLS_DESCR_VALUE_T type.

#### CYBLE_EVT_GLSC_WRITE_DESCR_RESPONSE
GLS Client - Write Response for Write Request of Glucose
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_GLS_DESCR_VALUE_T type.

### HIDS Service Events

#### CYBLE_EVT_HIDSS_NOTIFICATION_ENABLED
HIDS Server - Notifications for HID service were
enabled. The parameter of this event is a 
structure of CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_NOTIFICATION_DISABLED
HIDS Server - Notifications for HID service were
disabled. The parameter of this event is a 
structure of CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_BOOT_MODE_ENTER
HIDS Server - Enter boot mode request. The
parameter of this event is a structure of
CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_REPORT_MODE_ENTER
HIDS Server - Enter report mode request. The
parameter of this event is a structure of
CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_SUSPEND
HIDS Server - Enter suspend mode request. The
parameter of this event is a structure of
CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_EXIT_SUSPEND
HIDS Server - Exit suspend mode request. The
parameter of this event is a structure of
CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSS_REPORT_CHAR_WRITE
HIDS Server - Write Report characteristic 
request. The parameter of this event is a
structure of CYBLE_HIDSS_REPORT_VALUE_T type.

#### CYBLE_EVT_HIDSC_NOTIFICATION
HIDS Client - HID Service Characteristic
Notification was received. The parameter of this
event is a structure of CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSC_READ_CHAR_RESPONSE
HIDS Client - Read Response for Read Request of HID
Service Characteristic value. The parameter of this
event is a structure of CYBLE_HIDS_DESCR_VALUE_T type.

#### CYBLE_EVT_HIDSC_WRITE_CHAR_RESPONSE
HIDS Client - Write Response for Write Request of
HID Service Characteristic value. The parameter
of this event is a structure of 
CYBLE_HIDS_CHAR_VALUE_T type.

#### CYBLE_EVT_HIDSC_READ_DESCR_RESPONSE
HIDS Client - Read Response for Read Request of HID
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of 
CYBLE_HIDS_DESCR_VALUE_T type.

#### CYBLE_EVT_HIDSC_WRITE_DESCR_RESPONSE
HIDS Client - Write Response for Write Request of HID
Service Characteristic Configuration Descriptor value. 
The parameter of this event is a structure of 
CYBLE_HIDS_CHAR_VALUE_T type.

### HTTP Proxy Service Events

#### CYBLE_EVT_HPSS_NOTIFICATION_ENABLED
HPS Server - Notification for HTTP Proxy Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_HPS_CHAR_VALUE_T type.

#### CYBLE_EVT_HPSS_NOTIFICATION_DISABLED
HPS Server - Notification for HTTP Proxy Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_HPS_CHAR_VALUE_T type.

#### CYBLE_EVT_HPSS_CHAR_WRITE
HPS Server - Write Request for HTTP Proxy Service
Characteristic was received. The parameter of this event is a structure of
CYBLE_HPS_CHAR_VALUE_T type.

#### CYBLE_EVT_HPSC_NOTIFICATION
HPS Client - HTTP Proxy Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_HPS_CHAR_VALUE_T type.

#### CYBLE_EVT_HPSC_READ_CHAR_RESPONSE
HPS Client - Read Response for Read Request of HTTP Proxy 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HPS_CHAR_VALUE_T type.

#### CYBLE_EVT_HPSC_READ_DESCR_RESPONSE
HPS Client - Read Response for Read Request of HTTP Proxy
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_HPS_DESCR_VALUE_T type.

#### CYBLE_EVT_HPSC_WRITE_DESCR_RESPONSE
HPS Client - Write Response for Write Request of HTTP Proxy
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_HPS_DESCR_VALUE_T type.

#### CYBLE_EVT_HPSC_WRITE_CHAR_RESPONSE
HPS Client - Write Response for Write Request of HPS 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HPS_CHAR_VALUE_T type.

### HRS Service Events

#### CYBLE_EVT_HRSS_ENERGY_EXPENDED_RESET
HRS Server - Reset Energy Expended. The parameter of 
this event is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSS_NOTIFICATION_ENABLED
HRS Server - Notification for Heart Rate Measurement
Characteristic was enabled. The parameter of this 
event is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSS_NOTIFICATION_DISABLED
HRS Server - Notification for Heart Rate Measurement
Characteristic was disabled. The parameter of this 
event is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSC_NOTIFICATION
HRS Client - Heart Rate Measurement Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSC_READ_CHAR_RESPONSE
HRS Client - Read Response for Read Request of HRS 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSC_WRITE_CHAR_RESPONSE
HRS Client - Write Response for Write Request of HRS 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSC_READ_DESCR_RESPONSE
HRS Client - Read Response for Read Request of HRS
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_HRS_CHAR_VALUE_T type.

#### CYBLE_EVT_HRSC_WRITE_DESCR_RESPONSE
HRS Client - Write Response for Write Request of HRS
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_HRS_CHAR_VALUE_T type.

### HTS Service Events

#### CYBLE_EVT_HTSS_NOTIFICATION_ENABLED
HTS Server - Notifications for Health Thermometer Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSS_NOTIFICATION_DISABLED
HTS Server - Notifications for Health Thermometer Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSS_INDICATION_ENABLED
HTS Server - Indication for Health Thermometer Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSS_INDICATION_DISABLED
HTS Server - Indication for Health Thermometer Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSS_INDICATION_CONFIRMED
HTS Server - Health Thermometer Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSS_CHAR_WRITE
HTS Server - Write Request for Health Thermometer Service Characteristic
was received. The parameter of this event is a structure
of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSC_NOTIFICATION
HTS Client - Health Thermometer Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSC_INDICATION
HTS Client - Health Thermometer Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSC_READ_CHAR_RESPONSE
HTS Client - Read Response for Read Request of Health Thermometer 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSC_WRITE_CHAR_RESPONSE
HTS Client - Write Response for Write Request of Health Thermometer 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_HTS_CHAR_VALUE_T type.

#### CYBLE_EVT_HTSC_READ_DESCR_RESPONSE
HTS Client - Read Response for Read Request of Health Thermometer
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_HTS_DESCR_VALUE_T type.

#### CYBLE_EVT_HTSC_WRITE_DESCR_RESPONSE
HTS Client - Write Response for Write Request of Health Thermometer
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_HTS_DESCR_VALUE_T type.

### Immediate Alert Service Events

#### CYBLE_EVT_IASS_WRITE_CHAR_CMD
IAS Server - Write command request for Alert Level
Characteristic. The parameter of this event
is a structure of CYBLE_IAS_CHAR_VALUE_T type.

### Indoor Positioning Service Events

#### CYBLE_EVT_IPSS_READ_CHAR
IPS Server - Read Request for Indoor Positioning Service Characteristic
was received. The parameter of this event is a structure
of CYBLE_IPSS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSS_WRITE_CHAR
IPS Server - Write Request for Indoor Positioning Service Characteristic
was received. The parameter of this event is a structure
of CYBLE_IPSS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSS_WRITE_CHAR_CMD
IPS Server - Write command request for Indoor Positioning Service
Characteristic. The parameter of this event
is a structure of CYBLE_IPSS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSC_READ_CHAR_RESPONSE
IPS Client - Read Response for Read Request of Indoor Positioning
Service Characteristic value. The parameter of this event
is a structure of CYBLE_IPS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSC_READ_MULTIPLE_CHAR_RESPONSE
IPS Client - Read Multiple Response for Read Multiple Request of 
Indoor Positioning Service Characteristic value. The parameter 
of this event is a structure of CYBLE_IPS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSC_WRITE_CHAR_RESPONSE
IPS Client - Write Response for Write Request of Indoor Positioning 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_IPS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSC_READ_DESCR_RESPONSE
IPS Client - Read Response for Read Request of Indoor Positioning
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_IPS_DESCR_VALUE_T type.

#### CYBLE_EVT_IPSC_WRITE_DESCR_RESPONSE
IPS Client - Write Response for Write Request of Indoor Positioning
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_IPS_DESCR_VALUE_T type.

#### CYBLE_EVT_IPSC_ERROR_RESPONSE
IPS Client - Error Response for Write Request for Indoor Positioning
Service Characteristic Value. The parameter of this event is a structure of 
CYBLE_IPS_CHAR_VALUE_T type.

#### CYBLE_EVT_IPSC_READ_BLOB_RSP
IPS Client - Read Response for Long Read Request of Indoor Positioning
Service Characteristic value. The parameter of this event
is a structure of CYBLE_IPS_CHAR_VALUE_T type.

### Link Loss Service Events

#### CYBLE_EVT_LLSS_WRITE_CHAR_REQ
LLS Server - Write request for Alert Level Characteristic. 
The parameter of this event is a structure of 
CYBLE_LLS_CHAR_VALUE_T type.

#### CYBLE_EVT_LLSC_READ_CHAR_RESPONSE
LLS Client - Read response for Alert Level Characteristic.
The parameter of this event is a structure of 
CYBLE_LLS_CHAR_VALUE_T type.

#### CYBLE_EVT_LLSC_WRITE_CHAR_RESPONSE
LLS Client - Write response for write request of Alert
Level Characteristic. The parameter of this event is a
structure of CYBLE_LLS_CHAR_VALUE_T type.

### Location and Navigation Service Events

#### CYBLE_EVT_LNSS_INDICATION_ENABLED
LNS Server - Indication for Location and Navigation Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSS_INDICATION_DISABLED
LNS Server - Indication for Location and Navigation Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSS_INDICATION_CONFIRMED
LNS Server - Location and Navigation Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSS_NOTIFICATION_ENABLED
LNS Server - Notifications for Location and Navigation Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSS_NOTIFICATION_DISABLED
LNS Server - Notifications for Location and Navigation Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSS_WRITE_CHAR
LNS Server - Write Request for Location and Navigation Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSC_INDICATION
LNS Client - Location and Navigation Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSC_NOTIFICATION
LNS Client - Location and Navigation Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSC_READ_CHAR_RESPONSE
LNS Client - Read Response for Read Request of Location and Navigation 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSC_WRITE_CHAR_RESPONSE
LNS Client - Write Response for Write Request of Location and Navigation 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_LNS_CHAR_VALUE_T type.

#### CYBLE_EVT_LNSC_READ_DESCR_RESPONSE
LNS Client - Read Response for Read Request of Location and Navigation
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_LNS_DESCR_VALUE_T type.

#### CYBLE_EVT_LNSC_WRITE_DESCR_RESPONSE
LNS Client - Write Response for Write Request of Location and Navigation
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_LNS_DESCR_VALUE_T type.

### Next DST Change Service Events

#### CYBLE_EVT_NDCSC_READ_CHAR_RESPONSE
NDCS Client - Read Response for Read Request of Next DST Change 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_NDCS_CHAR_VALUE_T type.

### Phone Alert Status Service Events

#### CYBLE_EVT_PASSS_NOTIFICATION_ENABLED
PASS Server - Notifications for Phone Alert Status Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSS_NOTIFICATION_DISABLED
PASS Server - Notifications for Phone Alert Status Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSS_WRITE_CHAR
PASS Server - Write Request for Phone Alert Status Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSC_NOTIFICATION
PASS Client - Phone Alert Status Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSC_READ_CHAR_RESPONSE
PASS Client - Read Response for Read Request of Phone Alert Status 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSC_WRITE_CHAR_RESPONSE
PASS Client - Write Response for Write Request of Phone Alert Status 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_PASS_CHAR_VALUE_T type.

#### CYBLE_EVT_PASSC_READ_DESCR_RESPONSE
PASS Client - Read Response for Read Request of Phone Alert Status
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_PASS_DESCR_VALUE_T type.

#### CYBLE_EVT_PASSC_WRITE_DESCR_RESPONSE
PASS Client - Write Response for Write Request of Phone Alert Status
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_PASS_DESCR_VALUE_T type.

### Running Speed and Cadence Service Events

#### CYBLE_EVT_RSCSS_NOTIFICATION_ENABLED
RSCS Server - Notifications for Running Speed and Cadence Service
Characteristic were enabled. The parameter of this event is a structure of
CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSS_NOTIFICATION_DISABLED
RSCS Server - Notifications for Running Speed and Cadence Service
Characteristic was disabled. The parameter of this event is a structure 
of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSS_INDICATION_ENABLED
RSCS Server - Indication for Running Speed and Cadence Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSS_INDICATION_DISABLED
RSCS Server - Indication for Running Speed and Cadence Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSS_INDICATION_CONFIRMATION
RSCS Server - Running Speed and Cadence Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSS_CHAR_WRITE
RSCS Server - Write Request for Running Speed and Cadence Service
Characteristic was received. The parameter of this event is a structure
of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSC_NOTIFICATION
RSCS Client - Running Speed and Cadence Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSC_INDICATION
RSCS Client - Running Speed and Cadence Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSC_READ_CHAR_RESPONSE
RSCS Client - Read Response for Read Request of Running Speed and Cadence 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSC_WRITE_CHAR_RESPONSE
RSCS Client - Write Response for Write Request of Running Speed and Cadence 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_RSCS_CHAR_VALUE_T type.

#### CYBLE_EVT_RSCSC_READ_DESCR_RESPONSE
RSCS Client - Read Response for Read Request of Running Speed and Cadence
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_RSCS_DESCR_VALUE_T type.

#### CYBLE_EVT_RSCSC_WRITE_DESCR_RESPONSE
RSCS Client - Write Response for Write Request of Running Speed and Cadence
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_RSCS_DESCR_VALUE_T type.

### Reference Time Update Service Events

#### CYBLE_EVT_RTUSS_WRITE_CHAR_CMD
RTUS Server - Write command request for Reference Time Update
Characteristic value. The parameter of this event
is a structure of CYBLE_RTUS_CHAR_VALUE_T type.

#### CYBLE_EVT_RTUSC_READ_CHAR_RESPONSE
RTUS Client - Read Response for Read Request of Reference Time Update
Service Characteristic value. The parameter of this event
is a structure of CYBLE_RTUS_CHAR_VALUE_T type.

### Scan Parameters Service Events

#### CYBLE_EVT_SCPSS_NOTIFICATION_ENABLED
ScPS Server - Notifications for Scan Refresh Characteristic
were enabled. The parameter of this event is a structure 
of CYBLE_SCPS_CHAR_VALUE_T type.

#### CYBLE_EVT_SCPSS_NOTIFICATION_DISABLED
ScPS Server - Notifications for Scan Refresh Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_SCPS_CHAR_VALUE_T type.

#### CYBLE_EVT_SCPSS_SCAN_INT_WIN_CHAR_WRITE
ScPS Client - Read Response for Scan Interval Window 
Characteristic Value of Scan Parameters Service. The 
parameter of this event is a structure 
of CYBLE_SCPS_CHAR_VALUE_T type.

#### CYBLE_EVT_SCPSC_NOTIFICATION
ScPS Client - Scan Refresh Characteristic Notification 
was received. The parameter of this event is a 
structure of CYBLE_SCPS_CHAR_VALUE_T type.

#### CYBLE_EVT_SCPSC_READ_DESCR_RESPONSE
ScPS Client - Read Response for Scan Refresh Characteristic
Descriptor Read Request. The parameter of this event is a
structure of CYBLE_SCPS_DESCR_VALUE_T type.

#### CYBLE_EVT_SCPSC_WRITE_DESCR_RESPONSE
ScPS Client - Write Response for Scan Refresh Client 
Characteristic Configuration Descriptor Value. The
parameter of this event is a structure of
CYBLE_SCPS_DESCR_VALUE_T type.

### Tx Power Service Events

#### CYBLE_EVT_TPSS_NOTIFICATION_ENABLED
TPS Server - Notification for Tx Power Level Characteristic
was enabled. The parameter of this event is a structure of
CYBLE_TPS_CHAR_VALUE_T type.

#### CYBLE_EVT_TPSS_NOTIFICATION_DISABLED
TPS Server - Notification for Tx Power Level Characteristic
was disabled. The parameter of this event is a structure of
CYBLE_TPS_CHAR_VALUE_T type.

#### CYBLE_EVT_TPSC_NOTIFICATION
TPS Client - Tx Power Level Characteristic Notification. 
The parameter of this event is a structure of
CYBLE_TPS_CHAR_VALUE_T type.

#### CYBLE_EVT_TPSC_READ_CHAR_RESPONSE
TPS Client - Read Response for Tx Power Level Characteristic
Value Read Request. The parameter of this event is a 
structure of CYBLE_TPS_CHAR_VALUE_T type.

#### CYBLE_EVT_TPSC_READ_DESCR_RESPONSE
TPS Client - Read Response for Tx Power Level Client 
Characteristic Configuration Descriptor Value Read Request. 
The parameter of this event is a structure of 
CYBLE_TPS_DESCR_VALUE_T type.

#### CYBLE_EVT_TPSC_WRITE_DESCR_RESPONSE
TPS Client - Write Response for Tx Power Level Characteristic
Descriptor Value Write Request. The parameter of this event
is a structure of CYBLE_TPS_DESCR_VALUE_T type.

### User Data Service Events

#### CYBLE_EVT_UDSS_INDICATION_ENABLED
UDS Server - Indication for User Data Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_INDICATION_DISABLED
UDS Server - Indication for User Data Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_INDICATION_CONFIRMED
UDS Server - User Data Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_NOTIFICATION_ENABLED
UDS Server - Notifications for User Data Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_NOTIFICATION_DISABLED
UDS Server - Notifications for User Data Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_READ_CHAR
UDS Server - Read Request for User Data Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSS_WRITE_CHAR
UDS Server - Write Request for User Data Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSC_INDICATION
UDS Client - User Data Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSC_NOTIFICATION
UDS Client - User Data Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSC_READ_CHAR_RESPONSE
UDS Client - Read Response for Read Request of User Data 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSC_WRITE_CHAR_RESPONSE
UDS Client - Write Response for Write Request of User Data 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_UDSC_READ_DESCR_RESPONSE
UDS Client - Read Response for Read Request of User Data
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_UDS_DESCR_VALUE_T type.

#### CYBLE_EVT_UDSC_WRITE_DESCR_RESPONSE
UDS Client - Write Response for Write Request of User Data
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_UDS_DESCR_VALUE_T type.

#### CYBLE_EVT_UDSC_ERROR_RESPONSE
UDS Client - Error Response for Write Request for User Data Service
Characteristic Value. The parameter of this event is a structure of 
CYBLE_UDS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_NOTIFICATION_ENABLED
WPTS Server - Notifications for Wireless Power Transfer Service Characteristic
were enabled. The parameter of this event is a structure of
CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_NOTIFICATION_DISABLED
WPTS Server - Notifications for Wireless Power Transfer Service Characteristic
were disabled. The parameter of this event is a structure 
of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_INDICATION_ENABLED
WPTS Server - Indication for Wireless Power Transfer Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_INDICATION_DISABLED
WPTS Server - Indication for Wireless Power Transfer Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_INDICATION_CONFIRMED
WPTS Server - Wireless Power Transfer Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSS_WRITE_CHAR
WPTS Server - Write Request for Wireless Power Transfer Service Characteristic 
was received. The parameter of this event is a structure
of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSC_NOTIFICATION
WPTS Client - Wireless Power Transfer Service Characteristic
Notification was received. The parameter of this event
is a structure of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSC_INDICATION
WPTS Client - Wireless Power Transfer Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSC_WRITE_CHAR_RESPONSE
WPTS Client - Write Response for Read Request of Wireless Power Transfer 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSC_READ_CHAR_RESPONSE
WPTS Client - Read Response for Read Request of Wireless Power Transfer 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_WPTS_CHAR_VALUE_T type.

#### CYBLE_EVT_WPTSC_READ_DESCR_RESPONSE
WPTS Client - Read Response for Read Request of Wireless Power Transfer
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_WPTS_DESCR_VALUE_T type.

#### CYBLE_EVT_WPTSC_WRITE_DESCR_RESPONSE
WPTS Client - Write Response for Write Request of Wireless Power Transfer
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_WPTS_DESCR_VALUE_T type.

#### CYBLE_EVT_WSSS_INDICATION_ENABLED
WSS Server - Indication for Weight Scale Service Characteristic
was enabled. The parameter of this event is a structure 
of CYBLE_WSS_CHAR_VALUE_T type.

#### CYBLE_EVT_WSSS_INDICATION_DISABLED
WSS Server - Indication for Weight Scale Service Characteristic
was disabled. The parameter of this event is a structure 
of CYBLE_WSS_CHAR_VALUE_T type.

#### CYBLE_EVT_WSSS_INDICATION_CONFIRMED
WSS Server - Weight Scale Service Characteristic
Indication was confirmed. The parameter of this event
is a structure of CYBLE_WSS_CHAR_VALUE_T type.

#### CYBLE_EVT_WSSC_INDICATION
WSS Client - Weight Scale Service Characteristic
Indication was received. The parameter of this event
is a structure of CYBLE_WSS_CHAR_VALUE_T type.

#### CYBLE_EVT_WSSC_READ_CHAR_RESPONSE
WSS Client - Read Response for Read Request of Weight Scale 
Service Characteristic value. The parameter of this event
is a structure of CYBLE_WSS_CHAR_VALUE_T type.

#### CYBLE_EVT_WSSC_READ_DESCR_RESPONSE
WSS Client - Read Response for Read Request of Weight Scale
Service Characteristic Descriptor Read request. The 
parameter of this event is a structure of
CYBLE_WSS_DESCR_VALUE_T type.

#### CYBLE_EVT_WSSC_WRITE_DESCR_RESPONSE
WSS Client - Write Response for Write Request of Weight Scale
Service Characteristic Configuration Descriptor value.
The parameter of this event is a structure of 
CYBLE_WSS_DESCR_VALUE_T type.
