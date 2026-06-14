# Medium Module

## Rogue Tower
This challenge gave us the pcap file of a suspicious cell tower and provided us with several hints.

### Solution
First I used wireshark to open the file. Then I followed the hints,
1. I identified the rogue tower as the UDP broadcasts on port 55000 contained:
UNAUTHORIZED-TEST-NETWORK
PLMN=00101
CELLID=91043
2. I then identified the device connected to the rogue tower by searching through the http packets and found one with the same CELLID
User-Agent: MobileDevice/1.0 (IMSI:310410187936156; CELL:91043)
thus, I also found the required IMSI
3. I then went through all the HTTP post requests and extracted all the data that they had to finally get
"534635615848566c6330314b4231354742573557425652625a6b634752675a455a774259417742585551466253673d3d"
4. This was basically a hex coded data, and so I decoded it to give SF5aXHVlc01KB15GBW5WBVRbZkcGRgZEZwBYAwBXUQFbSg==
5. Since it was mentioned that the IMSI would be useful for encryption, I tried different methods of XOR using the IMSI with the decoded chunk to try and find out the flag.
6. Finally, running repeated XOR using the last 8 digits of the IMSI key gave me the flag.
  

```
wireshark rogue_tower.pcap
```

### Flag
> picoCTF{r0gu3_c3ll_t0w3r_7a06fd7c}

### Resources
Google, Ubuntu, Wireshark
