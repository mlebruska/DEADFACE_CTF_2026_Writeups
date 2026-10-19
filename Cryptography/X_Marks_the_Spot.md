# X Marks the Spot

## Objective

Given a hex-encoded payload, need to decrypt it:

```
02362b2964302c2164372c25202b3337642b226417342127303621641021272c2a2b282b233d7e6420212520222527213f3c2b361b751b263d30771b70301b701b3075297739
```

## The Solve

The first thing I did was plug the string into CyberChef's From Hex, which spit out an unreadable output.

My next step was to use CyberChef's "Magic" option with the crib "deadface" and Intensive mode enabled. This spit out the string

```
From the shadows of Spectre Technology: deadface{xor_1_byt3_4t_4_t1m3}
```

Which was a result of an XOR with the Hex value 44 (or the UTF8 value D).

Thus the flag is

```
deadface{xor_1_byt3_4t_4_t1m3}
```
