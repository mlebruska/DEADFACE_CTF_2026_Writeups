# DECODE-DLE

## Objective

Given a PNG called Decoddle.png, figure out a 3-digit lock combination based on the previous attempts.

In the image, I can see there are 5 previous attempts:

1. 8   6   3           <- One number is correct but in the wrong place

2. 2   5   0           <- Nothing is correct

3. 1   6   8           <- Two numbers are correct but in the wrong place

4. 7   3   5           <- One number is correct and in the right place

5. 6   8   7           <- Two numbers are correct but in the wrong place

## The Solve

Here is my thought process:

- Given lines 1 and 3, I know that:
    - 1 is part of the flag, but not in the first position (since 6 OR 8 is part of the flag, not both)
    - 3 is NOT part of the flag, since one of 6 or 8 is part of the flag (per line 3)
- Given the above and lines 2 and 4:
    - 7 is part of the flag and is in the first position since neither 3 nor 5 are in the flag
- Given lines 1, 3, and 5
    - 8 is NOT part of the flag, since it has appeared in all possible positions and each time there are no numbers in the correct position
- Given all of the above, the flag is:
    - 7 in the first position
    - 1 in the second position
    - 6 in the final position

Thus, the flag is

```
deadface{716}
```
