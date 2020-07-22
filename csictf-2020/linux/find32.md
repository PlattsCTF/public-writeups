## Find32

### Writeup by Trent (teerix)

Category: Linux

```
I should have really named my files better. I thought I've hidden the flag, now I can't find it myself. (Wrap your flag in csictf{})

ssh user1@chall.csivit.com -p 30630 Password is find32
```

Upon sshing and listing your current directory, you are greeted with a bunch of text files with random names and content. Performing `grep -Ril "csictf"` narrowed it down to one file, `MITS1KT3`.

When the file is viewed, it is apparent that the flag within is fake, but next to the fake flag is the string `{user2:AAE976A5232713355D58584CFE5A5}`.

Switching to "user2" using the value associated with it in the string for its password gives you access to user2's home folder files, with 5 files that all seem like the same dictionary wordlist.

When `wc -l` is performed on each of the 5 files, the result is that the "sadsas.tx" file is 1 line greater than the other 4.

Performing `diff [any of the other 4 files] sadsas.tx` results in th15_15_unu5u41 being returned. Wrap it up in flag tags and you have your flag!


Flag: csictf{th15_15_unu5u41}
