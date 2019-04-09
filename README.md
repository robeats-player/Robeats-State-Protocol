# Robeats-State-Protocol
The packets are defined with a packet number, written in hexadecimal notation prefixed by '0x' for convenience. Typically, packets prefixed 0x0 (values between 0 and 255) are packets for requesting state, and packets prefixed 0x1 (256 and upwards) are for returning state.

The packets are as follows:

The total size of this frame is 18bytes

|Request ID|Device ID|Device name|
|-|
|1 byte|1 byte|16 byte|



| Request ID| name | Description|
| ----------| ---------------------------------------------------------------------|
| 0x001     |Device Discovery| Ask devices on the same multicast socket to send their device information (see table above).|
| 0x002     |Request songlist| Request md5 hashes. Using Unicast (ip to ip).|
| 0x102     |Reply songlist|Response to `request songlist`. Sends a byte array with the md5 hashes of the songs to compare in unicast.|
| 0xF     |Sync confirm|Send a confirmation that the songs have been successfully synchronized in unicast.|
