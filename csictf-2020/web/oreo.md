## Oreo

### Writeup by Trent (teerix)

Category: Web

```
My nephew is a fussy eater and is only willing to eat chocolate oreo. Any other flavour and he throws a tantrum.

http://chall.csivit.com:30243
```

I opened the dev console and looked at the cookies stored, based on name of the challenge.

There was a cookie named 'flavour' with the value `c3RyYXdiZXJyeQ%3D%3D`

%3D is the HTML encoding of '=', making this seem like base64 encoding

Using `echo 'c3RyYXdiZXJyeQ==' | base64 -d` resolves the string to 'strawberry'

The base64 encoding of 'chocolate' is Y2hvY29sYXRl. Modifying the flavour cookie to that gives us the flag!


Flag: csictf{1ick_twi5t_dunk}