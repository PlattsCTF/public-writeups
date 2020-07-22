## Pwn Intended 0x1

### Writeup by Trent (teerix)

Category: Pwn

```
I really want to have some coffee!

nc chall.csivit.com 30001

File included: pwn-intended-0x1 Binary
```

The netcat shell starts with the ELF file included with the challenge. Typing in any input that is small returns a "Thanks!" and the
executable exits. Just to test for segmentation faults (and buffer overflows from that), I simply typed a very long string of As, which
returned that the coffee spilled, along with the flag below! 

Afternote: The source file of the challenge has a 30 byte string buffer where `gets()` is called and a "floor" integer, which calls the flag if it is changed to a non-zero number. Overwriting anything > 30 bytes would have given the flag.


Flag: csictf{y0u_ov3rfl0w3d_th@t_c0ff33_l1ke_@_buff3r}
