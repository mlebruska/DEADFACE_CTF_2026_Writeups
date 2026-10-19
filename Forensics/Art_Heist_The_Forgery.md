# Art Heist: The Forgery

## Objective

Identify the forged painting and recover the flag

## The Solve

I unzipped CTF_Forgery_Paintings.zip and did a bit of poking around with all of them.

```
file Painting_00*
```

showed them all to be PNG image data, 1024 x 1024, 8-bit/color RGB, non-interlaced

```
binwalk Painting_00*
```

found nothing (it actually claimed there to be MySQL ISAM index file Version 9 within Painting_005.png, but that ended up being nothing)

```
exiftool Painting_00*
```

showed descriptions of each of the paintings. Notably, the results for Painting_002.png contained the lines

```
Creator                         : Leonardo da Vinci / LAMIA
Description                     : Authenticity status: pending. Restoration log incomplete.
Identifier                      : deadface{L4MIA_SIGNS_HER_WORK}
Rights                          : LAMIA temporary acquisition
```

Thus the flag is

```
deadface{L4MIA_SIGNS_HER_WORK}
```
