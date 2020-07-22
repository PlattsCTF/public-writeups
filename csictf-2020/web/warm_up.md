## Warm Up

### Writeup by Trent (teerix)

Category: Web

```
If you know, you know; otherwise you might waste a lot of time.

http://chall.csivit.com:30272
```


Upon entering the given website, you are greeted with the back-end PHP script running on the site:

```
 <?php

if (isset($_GET['hash'])) {
    if ($_GET['hash'] === "10932435112") {
        die('Not so easy mate.');
    }

    $hash = sha1($_GET['hash']);
    $target = sha1(10932435112);
    if($hash == $target) {
        include('flag.php');
        print $flag;
    } else {
        print "csictf{loser}";
    }
} else {
    show_source(__FILE__);
}

?>
```

Our goal is to pass the script a value that when hashed with SHA1, is evaluated as equal to the SHA1 hash of 10932435112, without being that number itself.

Researching "10932435112 SHA1" brought up some interesting resources about magic hashes in PHP, which are linked at the bottom.

TL;DR: If comparisons on hashes are not done strictly using `===`, any hash that is a zeroed scientific notation (ex: 0e123), is evaluated as a flat zero.

The SHA1 hash of the above number is 0e077...2244, so it fits for this attack! Now we just find a second value that evaluates to a zeroed scientific notation, which
I used `AAJd1x3j` from the second resource below.

Once I input `http://chall.csivit.com:30272/?hash=AAJd1x3j` as the URL, I was brought to the flag!


Flag: csictf{typ3_juggl1ng_1n_php}


Resources:
https://www.whitehatsec.com/blog/magic-hashes/
https://derbenoo.github.io/cheat-sheet/2017/09/23/php/