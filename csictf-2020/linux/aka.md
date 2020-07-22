## AKA

### Writeup by Trent (teerix)

Category: Linux

```
Cows are following me everywhere I go. Help, I'm trapped!

nc chall.csivit.com 30611
```

Any linux command that is useful in navigating a shell results in the 'cowsay' command due to aliasing being implemented. To bypass this 'command' was prefixed on my commands implicitly state the command I wished to use.

`command ls` showed me that there was a flag.txt file. Upon issuing `command cat flag.txt`, the flag was shown.


Flag: csictf{1_4m_cl4rk3_k3nt}
