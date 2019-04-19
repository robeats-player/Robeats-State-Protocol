# Robeats-State-Protocol

### Multicast

`224.5.6.7` for IPv4 and `FF02::5:6:7` for IPv6 as multicast address.
We currently use IPv4 but is easily changed to IPv6

### Ports
Everything below 2000 is marked as reserved.
We will be using 4567 for device discovery (UDP) and 4568 for syncing hashes (TCP)

### File transfer

the File Transfer Protocol (https://tools.ietf.org/html/rfc959) will be used for transfering the files between users.

### The packets are as follows:

The total size of this segment is 18 bytes.


|Request ID|Device ID|Device name|
|-|-|-|
|1 byte|1 byte|16 byte|


The packets are defined with a request ID, written in hexadecimal notation prefixed by '0x' for convenience.

| Request ID| name | Description|
| ----------| -----|------------|
| 0x01     |Device Discovery| Ask devices on the same multicast socket to send their device information (see table above).|
| 0x11     |Device Discovery Reply| Reply to the discovery by sending an UDP using Unicast (ip to ip).|
| 0x02     |Request songlist| Request md5 hashes. Using Unicast.|
| 0x12     |Reply songlist|Response to `request songlist`. Sends a byte array with the md5 hashes of the songs to compare in unicast.|
| 0xFF      |Sync confirm|Send a confirmation that the songs have been successfully synchronized in unicast.|
