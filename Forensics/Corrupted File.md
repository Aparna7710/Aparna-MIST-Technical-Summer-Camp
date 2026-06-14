# Easy Module

## Corrupted file
This problem presented us with a non descript file that had been fully corrupted and which couldnt be opened on its own and gave us the hint to look to the bytes of the code for the solution. 

### Solution
I initially used the files command to try to figure out what type of file I had and that unfortunately led nowhere. I then used exiftool to look through the metadata and once again could not find anything useful. So, 
I followed the given hint about observing the file header using xxd command. Here I noticed JFIF which said to me that the file was a jpeg/jpg. However, when I googled the header that I got, I realised that the file
was not following the expected pattern for an image. Usually images start like "ff d8 ff e0" etc.. but this file started with "5c78 ffe0 0010 4a46 4946 0001 0100 0001" which said me immediately that the first two
bites had been corrupted making the file unreadable. Thus i then created a copy of the file, and ran a command on the copied file to change the first two bits into the proper format. After this, I used xdg command to 
open the cleaned image and thus retrieved the required flag.

```
files file
exiftool file
xxd file | head 
cp file file_copy
printf '\xFF\xD8' | dd of=file_copy bs = 1 count = 2 conv = nottrunc
xdg-open file_copy
```

### Flag
> picoCTF{rest0r1ing_th3_by73s_684e09bc}

### Resources
Ubuntu, Google, Exiftool, Binwalk.
