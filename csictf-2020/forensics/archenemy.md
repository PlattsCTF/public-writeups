## Archenemy

### Writeup by Trent (teerix)

Category: Forensics

```
John likes Arch Linux. What is he hiding?

File Included: arched.png
```

Upon placing the file into steghide I was given what initially looked like junk, but at the
end was written "We will, we will ROCKYOU", and the beginning had `PK` which is the file signature for a ZIP file.

Upon saving the output as a zip file, the unzip process gave a password prompt. I used the rockyou dictionary to find the password, as per the hint at the end:

`fcrackzip -u -D -p rockyou.txt flag.zip`

Enclosed was a JPG with the flag.


Flag: csictf{1_h0pe_y0u_don't_s33_m3_here}
