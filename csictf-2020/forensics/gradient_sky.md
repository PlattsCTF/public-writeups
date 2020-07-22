## Gradient Sky

### Writeup by Trent (teerix)

Category: Forensics

```
Gradient sky is a begginer level ctf challenge which is aimed towards rookies.

File Included: sky.jpg
```

Executing `binwalk -B sky.jpg` showed that there are magic bytes denoting a RAR file at offset 0x4807e (295038)

This file was extracted using dd: `dd if=sky.jpg of=sky.rar bs=1 skip=295038`

Upon unrar use, the file ls.txt was received. Opening the file reveals the flag


Flag: csictf{j0ker_w4snt_happy}
