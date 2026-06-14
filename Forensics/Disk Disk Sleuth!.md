# Medium Module

## Disk Disk Sleuth
This challenge asked us to use srch_strings and terminal flu to find the flag within the disk image.

### Solution
Going by the hints, I first of checked what kind of file it was and got this 'dds1-alpine.flag.img/dds1-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors'
which basically just indicated to me that it was a disk image. I then researched into the concept of srch_string command and terminal flu and I essentially understood that they are just more sorted and ordered
methods of filtering and searching the data. The intial command I used came up with an excessively huge amount of code, so I added more parameters to increase filtering and found the flag.

```
file dds1-alpine.flag.img/dds1-alpine.flag.img
srch_strings dds1-alpine.flag.img/dds1-alpine.flag.img | grep -i flag
srch_strings dds1-alpine.flag.img/dds1-alpine.flag.img | grep -Ei 'flag|ctf|pico|key' | tail -50
```

### Flag
> picoCTF{f0r3ns1c4t0r_n30phyt3_5e56e786}}

### Resources
Google, Ubuntu
