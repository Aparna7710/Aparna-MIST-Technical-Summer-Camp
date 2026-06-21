# Web Server module

## HTTP IP Restrictions Bypass
This challenge basically required us to be connected to the company intranet to access the site and thus thought us how to bypass network restrictions.

### Solution
On opening the provided site, the error message "Your IP ::ffff:103.214.63.212 do not belong to the LAN." immediately said me that I needed to somehow change the IP address to the required one to re-route and access this site. 
To try and do this, I took the help of google and found a service called Burp Suite which allows a user to intercept and re-route the site. Thus I then used this service and the command "X-Forwarded-For:" to access the site. 
Initially, I tried the IP address "X-Forwarded-For: 127.0.0.1" but got the new error message "Your IP 127.0.0.1 do not belong to the LAN.".
This confirmed that the server trusted the value supplied in the X-Forwarded-For header.
So, I then changed it to a private LAN address "X-Forwarded-For: 192.168.1.1" and this changed the site and immediately gave me the required password.


### Flag
> Ip_$po0Fing

### Resources
Google, Burp Suite
