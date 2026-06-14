# Easy Module

## RED
This challenge just gave us a red png and we had to find the hidden data.

### Solution
Strings command was used on the png and a poem was obtained which went as follows,
"Crimson heart, vibrant and bold,
Hearts flutter at your sight.
Evenings glow softly red,
Cherries burst with sweet life.
Kisses linger with your warmth. 
Love deep as merlot.
Scarlet leaves falling softly,
Bold in every stroke"
Collecting all the capital letters, we get the hint CHECKLSB which asks us to look at the least significant bit of the image. Thus I ran zsteg inspection on the image and retrieved another base 64 encoded message.
"cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="
When decoded, this message contained the flag which was repeated 4 times.

```
strings red.png
zsteg red.png
```

### Flag
> picoCTF{r3d_1s_th3_ult1m4t3_cur3_for_54dn355}

### Resources
Google, ubuntu, zsteg
