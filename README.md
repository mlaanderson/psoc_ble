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

### Generic Events

#### CYBLE_EVT_HOST_INVALID
This event is triggered by BLE stack when stack is in a bad state, restarting stack is the only way to get out
of the state.

#### CYBLE_EVT_STACK_ON
This event is received when BLE stack is initialized and turned ON by invoking CyBle_StackInit () function.

#### CYBLE_EVT_TIMEOUT
This event is received when there is a timeout and application needs to handle the event. Timeout reason is
defined by CYBLE_TO_REASON_CODE_T.

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

### GAP Events

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
CYBLE_GAP_AUTH_FAILED_REASON_T indicates the reason for failure.

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
 MP negotiated auth info event is raised as soon as SMP has completed pairing properties (feature exchange)
negotiation. The event parameter is CYBLE_GAP_AUTH_INFO_T. CYBLE_GAP_AUTH_INFO_T will have the 
negotiated parameter, the pairing should either pass with these negotiated parameters or may fail. This event
is applicable to both GAP Central and GAP Peripheral devices. In GAP Peripheral, this event is called from 
API-CyBle_GappAuthReqReply context.

#### CYBLE_EVT_GATTC_ERROR_RSP
#### CYBLE_EVT_GATT_CONNECT_IND
#### CYBLE_EVT_GATT_DISCONNECT_IND
#### CYBLE_EVT_GATTS_XCNHG_MTU_REQ
#### CYBLE_EVT_GATTC_XCHNG_MTU_RSP
#### CYBLE_EVT_GATTC_READ_BY_GROUP_TYPE_RSP
#### CYBLE_EVT_GATTC_READ_BY_TYPE_RSP
#### CYBLE_EVT_GATTC_FIND_INFO_RSP
#### CYBLE_EVT_GATTC_FIND_BY_TYPE_VALUE_RSP
#### CYBLE_EVT_GATTC_READ_RSP
#### CYBLE_EVT_GATTC_READ_BLOB_RSP
#### CYBLE_EVT_GATTC_READ_MULTI_RSP
#### CYBLE_EVT_GATTS_WRITE_REQ
#### CYBLE_EVT_GATTC_WRITE_RSP
#### CYBLE_EVT_GATTS_WRITE_CMD_REQ
#### CYBLE_EVT_GATTS_PREP_WRITE_REQ
#### CYBLE_EVT_GATTS_EXEC_WRITE_REQ
#### CYBLE_EVT_GATTC_EXEC_WRITE_RSP
#### CYBLE_EVT_GATTC_HANDLE_VALUE_NTF
#### CYBLE_EVT_GATTC_HANDLE_VALUE_IND
#### CYBLE_EVT_GATTS_HANDLE_VALUE_CNF
#### CYBLE_EVT_GATTS_DATA_SIGNED_CMD_REQ
#### CYBLE_EVT_GATTC_STOP_CMD_COMPLETE
#### CYBLE_EVT_GATTS_READ_CHAR_VAL_ACCESS_REQ
#### CYBLE_EVT_GATTC_LONG_PROCEDURE_END
#### CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_REQ
#### CYBLE_EVT_L2CAP_CONN_PARAM_UPDATE_RSP
#### CYBLE_EVT_L2CAP_COMMAND_REJ
#### CYBLE_EVT_L2CAP_CBFC_CONN_IND
#### CYBLE_EVT_L2CAP_CBFC_CONN_CNF
#### CYBLE_EVT_L2CAP_CBFC_DISCONN_IND
#### CYBLE_EVT_L2CAP_CBFC_DISCONN_CNF
#### CYBLE_EVT_L2CAP_CBFC_DATA_READ
#### CYBLE_EVT_L2CAP_CBFC_RX_CREDIT_IND
#### CYBLE_EVT_L2CAP_CBFC_TX_CREDIT_IND
#### CYBLE_EVT_L2CAP_CBFC_DATA_WRITE_IND
#### CYBLE_EVT_QUAL_SMP_PAIRING_REQ_RSP
#### CYBLE_EVT_QUAL_SMP_LOCAL_PUBLIC_KEY
#### CYBLE_EVT_QUAL_SMP_PAIRING_FAILED_CMD
#### CYBLE_EVT_PENDING_FLASH_WRITE
#### CYBLE_EVT_LE_PING_AUTH_TIMEOUT
#### CYBLE_EVT_MAX
