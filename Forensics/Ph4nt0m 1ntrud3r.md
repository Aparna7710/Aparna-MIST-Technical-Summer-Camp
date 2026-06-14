# Easy module

## Ph4nt0m 1ntrud3r
This challenge provided us with a pcap file and we were required to find the digital intruder who had entered the network.

### Solution
Given that we had a pcap file, I instantly used wireshark. The wireshark window opened and I was thus able to see 22 packets which followed the TCP protocol. At the end of each package there were characters like
"X5w4OZo=" which looked to be base64 encoded. Thus I collected all such characters from all 22 packages and obtained this,
```
"X5w4OZo=
H7DUfjk=
ob0o5i0=
y50ZdmI=
y1vZtpY=
hBFmx3U=
b0gkDEE=
fQ==
cGljb0NU
Rg==
8WXUPlw=
KWH98Vc=
kpRM1Ck=
ZTEwZTgz
OQ==
6dmdW8U=
XzM0c3lf
dA==
FNoN3tc=
bnRfdGg0
dA==
LJzhGLY=
tXcY/Ew=
YmhfNHJf
OA==
ezF0X3c0
cw== 
FUiWx28=
"
```
I then decoded this to get the flag.
```
wireshark myNetworkTraffic.pcap
```

### Flag
> picoCTF{1t_w4snt_th4t_34sy_tbh_4r_8e10e839}

### Resources
Ubuntu, Google, wireshark
