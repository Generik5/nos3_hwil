# Changes to treatment0 script

## Info:
- Running on the dev branch of NOS3
- COSMOS version 4.5.0

## Structure:
X. Change number

&nbsp;&nbsp;&nbsp;&nbsp;X. Line number in script

## Changes:

1. Had to comment out this line, do not have the `cfdp_up.rb` or `cfdp_down.rb` script

&nbsp;&nbsp;&nbsp;&nbsp;15. `#start("tests/cfdp_up.rb")`

2. Changed `DEST_IP` to match my setup... unsure if this is correct.

### Before:
&nbsp;&nbsp;&nbsp;&nbsp;8. `cmd("CFS_RADIO TO_ENABLE_OUTPUT with DEST_IP '127.0.0.1', DEST_PORT 5011")`

### After:
&nbsp;&nbsp;&nbsp;&nbsp;8. `cmd("CFS_RADIO TO_ENABLE_OUTPUT with DEST_IP '172.23.0.4', DEST_PORT 5011")`

3. Comment out `cfdp_up.rb` or `cfdp_down.rb` script

&nbsp;&nbsp;&nbsp;&nbsp;131. `#start("tests/cfdp_down.rb")`

&nbsp;&nbsp;&nbsp;&nbsp;136. `#start("tests/cfdp_up.rb")`

4. This command seems to have changed. Checked the docs and git commit history to see if there was any documentation of a change, but could not find any. This was the closest thing I could find in Command Sender.

### Before:
&nbsp;&nbsp;&nbsp;&nbsp;68. `cmd("NOVATEL_OEM615_RADIO NOVATEL_GPS_REQ_DATA_CC")`

### After:
&nbsp;&nbsp;&nbsp;&nbsp;68. `cmd("NOVATEL_OEM615_RADIO NOVATEL_OEM615_REQ_DATA")`

5. Same as change 4.

### Before:
&nbsp;&nbsp;&nbsp;&nbsp;123. `cmd("NOVATEL_OEM615_RADIO NOVATEL_GPS_NOOP_CC")`

### After:
&nbsp;&nbsp;&nbsp;&nbsp;123. `cmd("NOVATEL_OEM615_RADIO NOVATEL_OEM615_NOOP_CC")`

6. Same. Checked the docs picked the closest one, not sure if its working as I don't see `CCSDS_SEQUENCE` incrementing in Packet Viewer.

### Before:
&nbsp;&nbsp;&nbsp;&nbsp;80. `CAM_CNT_START = tlm("ARDUCAM_RADIO ARDUCAM_EXP_TLM_T CCSDS_SEQ_COUNT")`

### Before:
&nbsp;&nbsp;&nbsp;&nbsp;82. `CAM_CNT_CURRENT = tlm("ARDUCAM_RADIO ARDUCAM_EXP_TLM_T CCSDS_SEQ_COUNT")`

### After:
&nbsp;&nbsp;&nbsp;&nbsp;80. `CAM_CNT_START = tlm("ARDUCAM_RADIO ARDUCAM_EXP_TLM_T CCSDS_SEQUENCE")`

### After:
&nbsp;&nbsp;&nbsp;&nbsp;82. `CAM_CNT_CURRENT = tlm("ARDUCAM_RADIO ARDUCAM_EXP_TLM_T CCSDS_SEQUENCE")`
