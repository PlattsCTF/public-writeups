## Panda

### Writeup by Trent (teerix)

Category: Forensics

```
I wanted to send this file to AJ1479 but I did not want anyone else to see what's inside it, so I protected it with a pin.

File Included: panda.zip
```

The zip file is password protected. Using fcrackzip with the rockyou wordlist, I found the password to the zip and opened it:

`fcrackzip -u -D -p rockyou.txt panda.zip`

Upon opening, you receive two JPG files, panda.jpg and panda1.jpg, with the latter being the same image but corrupted in some
areas.

I initially tried LSB stegonography on the latter pic but it didn't work. Then, I decided to simply compare the differing bytes
of the two pictures using `cmp -l panda.jpg panda1.jpg` and found some bytes differed. When examining a few of the numbers, I realized the first few of the differing
bytes of the panda1.jpg picture spelled out 'csi' in octal.

I created this quick script to extract the flag:

```py
with open('compare.txt', 'r') as f:
        diff_list = f.readlines()

for i, j in enumerate(diff_list):
        diff_list[i] = j.strip().replace('  ',' ').split()



string = ''

for n in diff_list:
        string += chr(int(n[2], 8))

print(string)
```


Flag: csictf{kung_fu_p4nd4}
