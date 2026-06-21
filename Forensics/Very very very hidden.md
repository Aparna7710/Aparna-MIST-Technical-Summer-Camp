# Hard Module

## Very very very hidden
This challenge presented us with a file about a lot of network information and we were supposed to retrieve the flag from it.

### Solution
This challenge has completely screwed me over so far. I looked through the network file intiially, and I found a few links relating to NothingSus. From there I got two pngs and I've been basically stuck since. I've tried zsteg, file spearating, online steganography checkers and nothing. I found what seemed to be a part of a flag but that ended up being a dead-end. Im currently trying to see if the github links would lead me to anything but I'm unsure of how to move further and I will update this writeup with my progress. 
1. I combed through the pcap file again to find references to all possible sites and I found that amazon aws, cloud flare, powershell and github were keep on re-occuring. I dismissed amazon aws since the requests seemed mundane. I searched the rest of the term. I kept searching for powershell github, cloudflare github with other prompts like image, decoding etc and finally through the ai prompt on google I ended up on the InvokePSI image repository.
2. Searching further on how to run the code, I ended up on another repo called Decode_PS_Stego and an attached blog file on how to run. However, for some reason, my system was unable to install it.
3. Thus, I again searched for alternatives and ended up on a python code.
4. Running this python code finally gave me something "$enc = [system.Text.Encoding]::UTF8
$string1 = "HEYWherE(IS_tNE)50uP?^DId_YOu(]E@t*mY_3RD()B2g3l?"
$string2 = "8,:8+14>Fx0l+$*KjVD>[o*.;+1|*[n&2G^201l&,Mv+_'T_B"
5. So I now, went to cyberchef, searched for UTF8 and did an XOR operation to finally get the flag. 

```
from PIL import Image
import os
import math

def extract_invoke_psimage(image_path, output_path):
    img = Image.open(image_path)
    width, height = img.size
    pixels = img.load()

    lmaxpayload = (width * height * 3) // 2
    rows = math.ceil(lmaxpayload / width)
    array_size = rows * width
    lrows = height - 1
    lwidth = width - 1
    lpayload = int(lmaxpayload - 1)

    payload_bytes = bytearray(array_size)

    for y in range(lrows + 1):
        for x in range(lwidth + 1):
            r, g, b = pixels[x, y][:3]
            byte = ((b & 0x0F) << 4) | (g & 0x0F)

            index = y * width + x
            if index < array_size:
                payload_bytes[index] = byte

    payload = payload_bytes[:lpayload + 1].decode("ascii", errors="ignore")

    with open(output_path, "w", encoding="utf-8") as f:
        f.write(payload)

    print("\n[+] Extraction complete")
    print(f"[+] Saved to: {output_path}")
    print("\n[+] First 500 characters:\n")
    print(payload[:500])

if __name__ == "__main__":
    print("Current directory:", os.getcwd())

    if not os.path.exists("evil_duck.png"):
        print("[-] evil_duck.png not found in current folder")
    else:
        extract_invoke_psimage(
            "evil_duck.png",
            "result.ps1"
        )
```

### Flag
> picoCTF{n1c3_job_f1nd1ng_th3_s3cr3t_in_the_im@g3}

### Resources
Google, chatgpt, ubuntu, wireshark, Jupyter Notebook (for the python code), Above mentioned github repos and a blogpost by GauthamV

