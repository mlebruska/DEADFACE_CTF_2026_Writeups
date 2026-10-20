# A Pirate's Life for Me: Part 1

## Objective

Investigate a PCAP from a cafe after large data breaches

## The Solve

I filtered traffic using CTRL+f and searching Packet Details for Strings containing "deadface{" and found a packet with User-Agent: SunstalkerDFBrower that had X-1-Trace-Part starting with the flag format. This wasn't the entire flag, so I then filtered for X-2, X-3 (using CTRL+f and searching Packet Details for Strings) and found multiple parts of the flag, the whole thing being:

```
deadface{X-M4rk5_th3_sp0t_I_gu355}
```
