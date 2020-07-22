## Mr. Rami

### Writeup by Trent (teerix)

Category: Crypto

```
The flag.zip contains the flag I am looking for but it is password protected. The password is the encrypted message which has to be 
correctly decrypted so I can useit to open the zip file. I tried using RSA but the zip doesn't open by it. 
Can you help me get the flag please?

Files Included: a.txt, flag.zip
```

The file a.txt give us the following values:
n = 64741
e = 42667
c = 32949

Upon factoring n into p and q, calculating d and unciphering c, you receive a 2 character string that uses UTF-8 characters, which will not open the zip file.

However, if the integer value itself of the string is used, it is decompressed and a txt file containing the flag.

Flag: csictf{gr34t_m1nds_th1nk_4l1ke}
