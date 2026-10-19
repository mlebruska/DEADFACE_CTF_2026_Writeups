# Hooked

## Objective

Identify suspicious URL clicked by a De Monne Financial employee clicked on (from a phishing email)

## The Solve

I unzipped CTF_Caches_Kampeter_1.zip and clicked around to see what there was. In the folder Cache, there were 9 files that seemed to contain HTTP information. Reading through them sequentially:

f_000001: VPN Setup Guide (nothing particularly suspicious)

f_000002: Finance Shared Documents 

f_000003: Markets | Reuters (no idea what's happening here)

f_000004: Accessing gmail (close, but not the actual phishing portion)

f_000005: contains PNG fake_gmail_logo (suspicious, but url doesn't end with the format ?param=value)

f_000006: Secure Employee Portal

This is what I was looking for. The url is in the format of the challenge description, and it follows a classic phishing plot of a fake company login. I also see that the image is called "demonne_logo_fake.png". Thus, the flag is the url:

```
deadface{http://demonne-secure-portal.net/login?ref=vpn_auth&token=df4e91bc}
```
