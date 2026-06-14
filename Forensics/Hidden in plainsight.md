# Easy Module

## Hidden in plainsight
This challenge gave us an image of what seemed to be a coding screen and we were required to find the flag through inspection of the image. 

### Solution
First, I used the strings command and immediately, a certain set of letters stood out to me in comparison to the rest "c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9". So, I put this string of text into google, found out it was base64
encoded and decoded it to reach the message "steghide:pAzzword" This immediately gave me the hint that I was supposed to use the steghide tool for further analysis. Therefore, I installed the tool and ran the 
corresponding extract command on the image and provided the password and hence I got a file with the flag.

On a side note, on noticing that the file was an image, I had immediately put it into Aperi'Solve to perform steganographic tests. But unfortunately, the site was taking a long time to respond and so I proceeded to 
do the above solution on my terminal. By the time I was done with the solution, the site had also finished loading and provided me with the same text file of the flag after all the tests.

```
strings img.jpg
steghide --extract -sf img.jpg
```

### Flag
> picoCTF{h1dd3n_1n_1m4g3s_656e4d79}

### Resources
Ubuntu, Google, Steghide.
