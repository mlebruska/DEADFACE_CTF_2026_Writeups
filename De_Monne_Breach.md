# Hostbusters

Note, I did not solve this entire series, below are my solves for the first four challenges. I am aware that the writeup is a bit out of order.

## PCAP Challenges

### Objective

#### Name to a Face

Analyze the PCAP file to fine the username from an SMB authentication attempt

#### Uninvited Guest

Analyze the PCAP file to find the IPv4 address of a suspicious answer after a resolvation attempt

### The Solve

#### Name to a Face

I viewed the PCAP file in Wireshark and filtered the input with

```
smb || smb2
```

From there, I can see numerous packets with the Info

```
Session Setup Request, NTLMSSP_AUTH, User: .\nkessler
```

nkessler is also the username of the compromised employee from the Memory Dump challenges. Thus the flag is

```
deadface{nkessler}
```

#### Uninvited Guest

I don't remember why I filtered for http traffic at the time, but it seemed logical to me in the moment. I found a packet with the Info

```
PROPFIND /executive HTTP/1.1 , NTLMSSP_AUTH, User: .\nkessler
```

Following the http stream yielded suspicious results, but the source and destination were in IPv6:

```
fe80::4632::93f:50be:fef3
fe80::5054:ff:fe77:6601
```

I ended up finding the MAC addresses for the source and destination:

```
52:54:00:77:20:01
52:54:00:77:66:01
```
I then filtered the packets to arp traffic and found the series of packet requests with

```
Who has 10.77.10.20? Tell 10.77.10.66
10.77.10.20 is at 52:54:00:77:20:01
```
The source for this request is 52:54:00:77:66:01, which is the MAC address corresponding to the IPv4 address we are looking for. It's IPv4 address, given the wording "Tell 10.77.10.66" is 10.77.10.66

Thus, the flag is

```
deadface{10.77.10.66}
```

## Memory Dump Challenges

### Objective

#### Who Goes There? 

Analyze the memory dump to find the username of a compromised De Monne Financial employee account

#### The Workstation in the Middle

Analyze the memory dump to determinne the compromised device's hostname

### The Solve

For Both Who Goes There? and The Workstation in the Middle, I used Volatility 3 Framework 2.28.2 to analyze the memory dump.

I tried a variety of options, but the solve for both of these ended up being

```
vol -f .\memory.raw windows.sessions
```

Which showed a variety of processes with the Address Data DMF-WS11-042/nkessler

Thus, the flag for Who Goes There? is

```
deadface{nkessler}
```

and the flag for The Workstation in the Middle is

```
deadface{DMF-WS11-042}
```
