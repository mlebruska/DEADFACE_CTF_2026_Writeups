# death

## Objective

Discover the real name of the DEADFACE leader d34th

## The Solve

### In ghosttown:

1. I searched for d34th on ghosttown and found a post from luciafer asking to post a picture of d34th on doomscroll (https://ghosttown.deadface.io/t/48/d34th-pls-explain-the-glasses).
2. During a search for a different challenge. I ran across a post where mirveal lists places someone could hide information in the doomscroll api (https://ghosttown.deadface.io/t/59/who-knew-doomscrolling-could-be-so-useful#post-691)

```
/api/posts/<id>/comments

/api/users/<id>/notes

/api/posts/<id>/meta

/api/feed/<id>/details

/api/posts/<id>/history
```

### On doomscroll

1. I searched for luciafer's profile and found the image discussed in the ghosttown post (https://doomscroll.dctf.ip/post/2OO).
2. Using id 200, I searched the api places and found that the /api/posts/200/meta page (doomscroll.dctf.io/api/posts/200/meta) contained the following:

```
{"meta":[{"id":1,"key":"filename","value":"travis_001.png","is_encrypted":0,"created_at":"2026-10-14 20:11:43","decrypted_value":null},{"id":2,"key":"what whaaaaat","value":"                                                                                                                                                                                                                                                                                                                        ","is_encrypted":0,"created_at":"2026-10-17 22:05:31","decrypted_value":null}]}
```

Seing that the filename for the image is "travis_001.png", I can guess that "Travis" is d34th's first name, thus the flag is:

```
deadface{Travis}
```

## Note

I originally posted this specific writeup as a pdf in the DEADFACE CTF discord writeup channel under the pseudonym "Sabre_girl", though I competed under the name "S4br3_G1rl"
