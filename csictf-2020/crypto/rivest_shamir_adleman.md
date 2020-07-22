## Rivest Shamir Adleman

### Writeup by Trent (teerix)

Category: Crypto

```
These 3 guys encrypted my flag, but they didn't tell me how to decrypt it.

File Included: enc.txt
```

The txt file included gives values for n, e, and c, which clearly corresponds to the RSA algorithm as the name suggests.

I found a tool for attacking n-values to attempt to factorize p and q out (as it is impossible to decrypt using
n, e, and c themselves).

I first created the public key, then attempted the crack to uncipher the text.

`./RsaCtfTool.py --createpub -n [the long n value] -e 65537 > key.pub`

`./RsaCtfTool.py --publickey ./key.pub --uncipher [the long c value]`

The resulting string was composed of a bunch of NULL hex values with the flag appended at the end


Flag: csictf{sh0uld'v3_t4k3n_b1gg3r_pr1m3s}


Resources:
https://github.com/Ganapati/RsaCtfTool
