# Infrequent Emojis

## Objecive

The objective for this challenge was to find and decrypt a DoomScroll post full of emojis.

## The Solve

Within doomscroll, I found the emoji post at https://doomscroll.dctf.io/post/252

The image was emojis in the flag format:

🪦🕯️💀🪦🩸💀(coffin)🕯️{🦉🕸️🕯️💀🌙🕯️_(bio)🔮🧪_🖤🌩️(bio)_⛓️🧪_🦇🕯️🔥_🌙(bio)💀🦇🪦💀🔮🪦}

I know that the flag will start with "deadface" and I was pretty sure this was a simple substitution cipher, so I can make the assingments

🪦 = d

🕯️ = e

💀 = a

🩸 = f

coffin = c

Thus the text is now:

deadface{🦉🕸️ea🌙e_🟡🔮🧪_🖤🌩️🟡_⛓️🧪_🦇e🔥_🌙🟡a🦇da🔮d}

At this point, the first and last words seem easy enough to guess: please and standard

deadface{please_tr🧪_🖤🌩️t_⛓️🧪_ne🔥_standard}

and after filling in the substitutions, I can guess the second word is try and the second to last word is new:

deadface{please_try_🖤🌩️t_⛓️y_new_standard}

with these substitutions, the third to last word is likly "my", and the third word (considering the letters I have left and the context of the sentence) is probably "out"

Thus the flag is

```
deadface{please_try_out_my_new_standard}
```
