## The Climb

### Writeup by Trent (teerix)

Category: Crypto

```
We are not lost, we're right here somewhere on this little blue line. Wait, why do I feel like I'm being watched?

File Included: theclimb.txt, theclimb.java
```

Upon running the java file, it shows a plaintext "fakeflag", a key "gybnqkurp", and the output of whatever cipher was used.

The text file contained a string of ciphertext, "lrzlhhombgichae".

The cipher being used is the Hill cipher, which was hinted at by the challenge title. I used the website in the resources for the remainder of the challenge.

First, I used the key from the java file to arrange a 3x3 matrix of numerical values, each cooresponding to the
zero-inclusive place value of the letter used. I then tested this matrix with our "fakeflag" plaintext to see if we got the
same ciphertext the application did, and we did!

Then, I simply placed the ciphertext in with the same matrix as the key, and decrypted it to "hillshaveeyesxx"

Removing the padding and wrapping it in flag tags gave us the flag.


Flag: csictf{hillshaveeyes}


Resources:
https://www.dcode.fr/hill-cipher
