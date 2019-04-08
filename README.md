# Robeats-State-Protocol
The packets are defined with a packet number, written in hexadecimal notation prefixed by '0x' for convenience. Typically, packets prefixed 0x0 (values between 0 and 255) are packets for requesting state, and packets prefixed 0x1 (256 and upwards) are for returning state.

The packets are as follows:

| Packet ID  | Description                                                           |
| ---------- | --------------------------------------------------------------------- |
| 0x001      | Broadcast packet, able and looking to sync.                           |
| 0x002      | Initialising a media sync, and requesting the checksums of all songs. |
| 0x102      | Response to 0x002, one checksum of one song. Multiple 0x102 packets will be sent until all songs' checksums have been sent, signified by an empty 0x102 packet. |
