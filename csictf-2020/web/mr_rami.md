## Mr. Rami

### Writeup by Trent (teerix)

Category: Web

```
"People who get violent get that way because they can’t communicate."

http://chall.csivit.com:30231
```

This challenge ended up in me going down a rabbit hole and took hours despite being very simple.

The website brings you to a very basic HTML site, with a link to a github for "BroBot", which was a telegram bot that I
played around with its `/shell` command to find anything hidden. 

After hours of this, I took a step back and looked at it from a WEB challenge standpoint.

I eventually realized that the challenge was simply to just look at the "robots.txt" file (hence the Mr. Robot reference) of the original website of the challenge, which gave a disallow path to `/fade/to/black`, which I went to and the flag was shown. 


Flag: csictf{br0b0t_1s_pr3tty_c00l_1_th1nk}
