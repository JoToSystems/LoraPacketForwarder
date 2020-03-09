# LoraPacketForwarder
Modified LoraPacket Forwarder to correct rejection on Transmit Power mismatch

The original Packet Forwarder would not transmit if the requested power from the Server (powe) did not match one of the entries in the Tx_lut table contained in global-config.json file

This version will search the Tx_lut table and select the next lowest power. 
