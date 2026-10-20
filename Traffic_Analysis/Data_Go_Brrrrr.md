# Data Go Brrrrr

## Objective

Find the flag within exfiltrated data

## The Solve

The PCAP file is rather short, and I can see a series of ICMP requests reaching from 192.168.1.20 to 10.10.14.7. In addition to the 10.10.14.7 being odd (in the context of the rest of the PCAP), each of these requests had non-standard bytes of data at the end:

```
ZGVhZGZh

Y2V7aWNt

cF8zeGZp

bF93aDNu

X3RoM3lf

bGVhc3Rf

c3VzcDNj

dH0=
```

Before every CTF, I make a point to see what the flag format looks in Base64. In this case, I recognized the opening as deadface in Base64, so I plugged everything I found into CyberChef (https://gchq.github.io/CyberChef/) using From Base64 and found:

```
deadface{icmp_3xfil_wh3n_th3y_least_susp3ct}
```
