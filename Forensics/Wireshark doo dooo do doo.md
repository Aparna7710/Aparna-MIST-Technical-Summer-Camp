# Medium Module

## Wireshark doo dooo do doo...
This challenge just gave us a pcang file to search for the flag.

### Solution
First I ran the command file to detect what type of file exactly I was dealing with since I was unfamiliar with this format. Then I opened it in wireshark. I made several mistakes in solving this problem initially
1. I first basic wireshark filtering like filtering by http, MIME etc and they all failed.
2. I then tried to search for names like flag, pico etc in the packets in wireshark and that also failed.
3. I tried exporting and inspecting all HTTP files but it was way larger than I intially expected.
4. I tried using string search and treating it like a huge string file or something.

Finally I resorted to the use of chatgpt to get a few hints since I was completely stuck. Then finally it gave me the hint to check for GET vs POST requests. So I applied the filter for checking GET requests in wireshark
and saw that there were only 2 get requests. I then expanded the HTTP column of one such request and was redirected to packet number 827 by a link. Here I got this code "cvpbPGS{c33xno00_1_f33_h_qrnqrors}" and
when I put it to google I realised it was ROT13 encoded. Thus I decoded it to get the flag.

```
bash
file shark1.pcapng

Wireshark display filter:

http.request.method == "GET"
```

### Flag
> picoCTF{p33kab00_1_s33_u_deadbeef}

### Resources
Ubuntu, ChatGpt, Wireshark, Google
