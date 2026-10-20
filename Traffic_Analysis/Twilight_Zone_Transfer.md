# Twilight Zone Transfer

## Objective

Find the unauthorized zone transfer which contains the flag

## The Solve

This was another short PCAP file. The challenge said that someone "pulled the ENTIRE zone in one request", and there was only one packet where a) the length was >200 and b) had an Info field that took up the entire screen. I followed the TCP stream and found the flag in the packet.

The flag was:

```
deadface{dns_zone_transfer}
```
