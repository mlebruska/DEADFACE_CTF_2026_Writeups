# Headshot

## Objective

Given the zip file headshot.zip, the goal is to find the image that was tampered with.

## The Solve

1. I unzipped headshot.zip which revealed 4 files: headshot001.png, headshot002.png, headshot003.png, and headshot003.png_original
2. The naming of the files tells me that #3 is the file that was tampered with
3. I ran a diff on headshot003.png and headshot003.png_original:

```
$ diff headshot003.png headshot003.png_original
Binary files headshot003.png and headshot003.png_original differ
```

4. Since this just said that the binary files differed, I ran strings on both files, saved the output to .txt files, and ran diff on those:

```
$ strings headshot003.png > alt.txt; strings headshot003.png_original > orig.txt; diff alt.txt orig.txt
22,23d21
< !tEXtComment
< deadface{b00m_h34Dsh0TTT}
```

Thus, the flag is

```
deadface{b00m_h34Dsh0TTT}
```
