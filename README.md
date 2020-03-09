# LoraPacketForwarder
Modified LoraPacket Forwarder to correct rejection on Transmit Power mismatch

The original Packet Forwarder would not transmit if the requested power from the Server (powe) did not match one of the entries in the Tx_lut table contained in global-config.json file

The Tx_lut table has a maximum of 16 entries but the LoraWan Server can request any power from -6dBm to +27dBm.  Even if the server is limited to the typical entries found in the global-config.json file, this is not a solution as the gateway's antenna gain is subtracted from the power requested by the Server and the resultant is checked against the Tx_lut table

An example of an error found in the gateway log file is
 ttn-gateway[xx]: ERROR: Packet REJECTED, unsupported RF power for TX - 24

This version will search the Tx_lut table and select the next lowest power. 

This version is compiled for a Raspberry Pi with the SPI running at 2MHz which is suitable for all verions of the SX1301 baseband chip including the RAK2245

