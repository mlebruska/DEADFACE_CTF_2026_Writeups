# Return to Sender

## Objective

Identify malicious web traffic and piece the flag together from stolen data

## The Solve

To be perfectly honest, I scrolled through the PCAP (it was short enough) and looked for anything that stood out. I found a packet from a weird IP (44.66.77.88) that was making a POST request to an api that nothing else used (/api/upload?seq=1 HTTP/1.1). Also, the data contained "ZGVhZGZh", which I know to be the start to "deadface" in Base64.

Using CTRL+F to search the Packet details for Strings matching "/api/upload", I found a total of 5 of these packets. The concatenated string of their data is

```
ZGVhZGZhY2V7aHR0cF9leGZpbF9zbmVha3lf
```

Using CyberChef's From Base64, this decodes to

```
deadface{http_exfil_sneaky_
```

Which clearly isn't the entire flag. I checked the rest of the packets and couldn't find anything, and it wasn't until I noticed that all the suspicious packets had the same X-Session-ID that I found the last part of the flag (YnVzaW5lc3N9)

Thus, the entire flag is 

```
deadface{http_exfil_sneaky_business}
```
