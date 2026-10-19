# Hail Caesar

## Objective

Given a PNG called pass_hint.png, objective is to extract a password by figuring out the name of the dog in the picture

In the image, I can see there is a drawing of a dog and the text

```
Zl qbt`f anzr vf Srgpu
```

## The Solve

Given the name of the challenge, I pulled up the dcode.fr Caesar Cipher (https://www.dcode.fr/caesar-cipher) and found that the phrase decodes to 

```
My dog`s name is Fetch
```

Thus, the flag is

```
deadface{Fetch}
```
